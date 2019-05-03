# VSCode Cloud Code Setting Example 

This sample python project is cloned from https://github.com/alicek106/nginx-ingress-annotation-text
## .vscode directory

- settings.json

  - **cloudcode.profile-cluster-map** : Settings of cloud code profiles. Custom Profiles can be edited in VSCode, but [default] profiles can be changed only in settings.json

  - Example : [default] profile is set to **'docker-for-mac'**

    ```
    {
        "cloudcode.profile-cluster-map": {
            "[default]": "docker-for-desktop",
            "cloudbuild": "test-kube",
            "test-kube": "test-kube"
        }
    }
    ```

  - **cloudcode.image-registry** : Registry name to use. skaffold automatically picks up this value to tag and push built image. But to let kubernetes cluster pull the image, **imagePullSecret (docker config type Secret) should be provided to Deployment.** 

  - Example : Below setting will trigger to build image with registry name, and push to registry.

    ```
    {
        "cloudcode.image-registry": {
            "name": "alicek106.ipdisk.co.kr"
        }
    }
    ```

    

- tasks.json

  - Settings for appropriate debugging and python interpreter. Below example uses src/app.py to launch application.

  - Example:

    ```
    {
        "version": "2.0.0",
        "tasks": [
            {
                "label": "Pylint",
                "type": "shell",
                "command": "python3",
                "args": ["-m", "pylint", "src/app.py"],
                "problemMatcher": []
            }
        ]
    }
    ```

    

## skaffold.yaml

- Attribute **profiles.build.local.push** can be true to push built image.

- Attribute **profiles.build.name** should be kubernetes profile name that you want to deploy.
