Step1.
First we should have the AWS account created or with IAM User you can login
=
<img width="1920" height="949" alt="Screenshot (11)" src="https://github.com/user-attachments/assets/dfe93707-7e5e-41b6-ab3d-b2fb8dc86903" />


Step2. Create a Lambda Function
=

**1.** Go to AWS Console → **Lambda** → **Create function**.

**2.** Choose:

   **Author from scratch**

   Function name: Myfunction

   Runtime: Python 3.x or Node.js 18


**3.** Add sample code (example in Python):

import json

def lambda_handler(event, context):
    return {
        "statusCode": 200,
        "body": json.dumps({"message": "Hello from Serverless API!"})
    }


**4.** Click **Deploy**.
<img width="1920" height="441" alt="image" src="https://github.com/user-attachments/assets/1160ae6d-857b-4a85-8aa8-ab5b78659337" />
<img width="1902" height="753" alt="image" src="https://github.com/user-attachments/assets/63939f5f-c64f-475b-a95b-9226c70dff6e" />
<img width="1902" height="762" alt="image" src="https://github.com/user-attachments/assets/87ba3820-f896-40b3-802a-1902eec71988" />








**Step2. Create an API Gateway**
=

**1.** Go to **Amazon API Gateway** → **Create API** →**REST API**.

**2.** Configure:

      API Name: Myapi

    Integration: Select Lambda Function → Myfunction.
    
<img width="1911" height="760" alt="image" src="https://github.com/user-attachments/assets/ceb67e21-caf2-4d0d-81e3-d0809f7a0dad" />


**3.** Click Deploy → Choose Stage: prod.

You now have an endpoint like:

       https://<myapi>.execute-api.<region>.amazonaws.com/prod/
<img width="1910" height="756" alt="image" src="https://github.com/user-attachments/assets/15da7958-fda4-4dc6-a174-c971a52962d3" />

<img width="1916" height="761" alt="image" src="https://github.com/user-attachments/assets/9c947b12-9876-4b4a-abc1-0e811f4ed54a" />

**4.**Output:
<img width="1920" height="306" alt="image" src="https://github.com/user-attachments/assets/e2491cd1-8281-4a66-b081-37b04a8498e0" />





Step3. Enable Lambda Versions & Aliases
=

**1.** Go to Lambda → Lambda-canary-Project.

**2.** Click Publish new version → Name it v1.

**3.** Create an Alias (e.g., prod) pointing to version v1.


Step 4. Canary Deployment Setup
=

A Canary deployment allows you to gradually shift traffic from one Lambda version to another.

**1.** In Lambda → Aliases → prod.

**2.** Click Edit traffic shifting.

**3.** Choose:

     Additional version: v2 (publish new version after code update).

     Traffic shifting: e.g., 10% to v2, 90% stays on v1.

**4.** Save changes.

Now requests hitting API Gateway → Lambda prod alias will be split between v1 and v2.

<img width="1908" height="752" alt="image" src="https://github.com/user-attachments/assets/1c7feeaf-f7ed-429c-9039-74e469bc25ba" />




Step 5. Test the Setup
=

**1.** Update Lambda with new code, publish as v2.

   


**2.** Invoke API Gateway endpoint:

           https://nlr0o6iuqk.execute-api.ap-south-1.amazonaws.com/prod


Some responses will show v2.
<img width="1920" height="279" alt="image" src="https://github.com/user-attachments/assets/d856b601-956e-4f35-80d5-df794390e870" />

