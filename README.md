# intro-pipeline-whstever
xercise 1.4 - Environment Directive
For Exercise 1.4 we are going to update our pipeline to demonstrate how to use the environment directive to set and use environment variables. We will also see how this directive supports a special helper method credentials() that allows access to pre-defined Jenkins Credentials based on their id.

Simple Environment Variables
At the top of the pipeline insert the following code between the agent and stages blocks:
   environment {
      MY_NAME = 'Mary'
   }
Then update the echo 'Hello World!' line to read echo "Hello ${MY_NAME}!"
Save & Run your pipeline and check the Console Log.
Notice the change from '' to "". Using double quotes will trigger extrapolation of environment variables.

Credentials
We can also use environmental variables to import credentials.

Add the following line to our environment block:
TEST_USER = credentials('test-user')

Add the following echo steps within the steps of the Say Hello stage:
            echo "${TEST_USER_USR}"
            echo "${TEST_USER_PSW}"
Note: After executing the build look at the console output and make note of the fact that the credential user name and password are masked when output via the echo command.

Exercise 1.5 - Parameters
In Exercise 1.5 we will alter our pipeline to accept external input in the form of a Parameter.

At the top of your pipeline insert the following block of code between the environment and stages blocks:
   parameters {
      string(name: 'Name', defaultValue: 'whoever you are', 
	     description: 'Who should I say hi to?')
   }
Update the echo "Hello ${MY_NAME}!' line to read echo "Hello ${params.Name}!"
Save & Run your pipline and view the results.
Note: Jenkins UI won't update properly when you save the pipeline to show the Build with parameters option so you need to run a build, view the results, and then return to the project to see the updated option.
