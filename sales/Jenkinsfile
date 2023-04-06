def sale(iterations)
{
    script
    {
        
        for(int i=0;i<iterations;++i)
        {
            catchError(stageResult: 'FAILURE')
            {
                str = 'python.exe ../AutomationTesting/Main.py -t 0 -ip 192.168.1.2 -vp ../AutomationTesting/validation/sale0.txt -a 23'
            
                bat str
            } 
        }
        
    }
}

def closeBatch(valPath)
{
    script
    {
            
        catchError(stageResult: 'FAILURE')
        {
            str = 'python.exe ../AutomationTesting/Main.py -t 0 -ip 192.168.1.2 -vp ' + valPath
            bat str
        }
    }
   
}

pipeline {
    agent any
  
    stages 
    {
        stage('closeBatchStart')
        {
            steps
            {
                closeBatch('../AutomationTesting/validation/closeBatch1.txt')
            }
        }
        stage('sale')
        {
            steps
            {

                sale(2)
            }
            
        }
        stage('close batch')
        {
            steps
            {
                 closeBatch('../AutomationTesting/validation/closeBatch.txt')
            }
        }
    }
}