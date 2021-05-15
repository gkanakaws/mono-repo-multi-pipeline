Question:
=======

I have a single github repository for multiple pipelines and any code change is triggering all the pipelines for different projects.
I was able to use the 'path' in the codebuild so that it would only build when a change for that projects root directory occurs. However, there is no such place on codepipeline. What should I do?

 - There is a feature request created already for advanced source filters in codepipeline however, I do not have an ETA on the release date.
 - For the GitHub repo, there is no cloudwatch event rule created automatically unlike for codecommit.
 - github webhook --> codepipeline webhook 
 - So you will have to include an additional custom source stage in the pipeline to trigger a cloudwatch event rule that triggers a lambda function to check the file changes and decide which codepipeline to trigger.
 - Please check this link [1] for the whole architecture of event driven method for the codepipeline.
 - This article talks about using lambda function with conditions to decide which pipeline to execute. Check the last part of the article - Multiple pipelines sourcing from a single repository.
