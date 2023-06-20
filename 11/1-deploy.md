# Session 11: Deploy CRA to Netlify

Here's a step-by-step guide on how to deploy code to Netlify:

1.  Add your code to Github:
    
    *   Create a new repository in Github for your code.
    *   Initialize the repository with a README file.
    *   Open the terminal and navigate to the root directory of your code.
    *   Run the following commands to add your code to the Github repository:
        
        ```bash
            git init
            git add .
            git commit -m "Initial commit"
            git remote add origin <your repository URL>
            git push -u origin master
        ```
        
2.  Deploy the code to Netlify:
    
    *   Go to the Netlify website and sign up for an account if you haven't already.
    *   Click on the "New site from Git" button.
    *   Select the "Github" option from the list of Git providers.
    *   Authorize Netlify to access your Github account.
    *   Select the repository that contains your code.
    *   Set the build options for your site, such as the build command and the publish directory.
    *   Click on the "Deploy site" button to start the deployment process.
    *   Once the deployment is complete, Netlify will provide you with a unique URL where you can access your site.

That's it! With these simple steps, you can deploy your code to Netlify and start taking advantage of the benefits of serverless deployment. If you have any questions or issues during the deployment process, Netlify provides a detailed documentation and support resources to help you resolve them.