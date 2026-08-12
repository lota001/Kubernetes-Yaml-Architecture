# Kubernetes Pod YAML Manifest

An implementation guide of a Kubernetes Pod manifest-built line by line to develop practical skills in YAML structure, indentation, configuration syntax, and Git version control. This project provides hands-on experience creating and managing Kubernetes configuration files using industry-standard DevOps practices.

## Topics Covered

- API version declaration
- Resource kind definition
- Nested metadata objects
- Lists and arrays for containers
- Proper YAML indentation and alignment
- Git version control and GitHub deployment

## Setup Project & Initialize Git

Create a dedicated working directory for the project and initialize a Git repository to enable version control. This establishes an organized workspace and allows you to track configuration changes, maintain a history of updates, and safely manage the project as it develops.

## 1. Create Project Directory

Creates a dedicated directory for your Kubernetes YAML configuration files, keeping infrastructure-as-code (IaC) resources organized and separate from unrelated project files. This structure makes configuration files easier to manage, maintain, version, and deploy as the project grows.

    ## Creates a new directory (folder).
    mkdir -p ~/yaml-architect && cd ~/yaml-architect

 <img width="831" height="81" alt="2026-08-12_10h26_25" src="https://github.com/user-attachments/assets/9463e2a4-683d-4029-8784-6177ab0eefa2" />

## 2. Initialize Git

Creates a hidden **.git** directory that stores the metadata required for Git version control. Git uses this repository data to track changes to your Kubernetes YAML manifests, allowing you to review modifications, restore previous versions, and maintain a reliable history throughout development.

    ## Initializes a new Git repository in the current directory.
    git init

<img width="835" height="105" alt="2026-08-12_10h27_03" src="https://github.com/user-attachments/assets/24d02580-7e9d-48c7-a909-355cccab8b39" />

## The Identity Key

Defines a simple key-value pair that specifies the Kubernetes API version used by the resource. The **_apiVersion_** field tells Kubernetes which API group and version should be used to interpret and validate the manifest.

## 1. Set API Version

Creates a **_pod.yaml_** manifest and defines **_apiVersion_** as its first key-value pair. This field tells Kubernetes which API group and version should be used to interpret, validate, and process the resource definition. Using the correct API version ensures Kubernetes understands the structure and supported fields in the manifest.

    ## Prints text to the terminal — also used to write to files with > or >>.
    echo "apiVersion: v1" > pod.yaml

<img width="839" height="83" alt="2026-08-12_10h28_38" src="https://github.com/user-attachments/assets/9a92fabf-176b-4ba7-a390-c82930cdb84f" />

## Naming the Kind

Adds the **_kind_** field as the second key-value pair to specify the type of Kubernetes resource being defined. For example, setting **_kind: Pod_** tells Kubernetes that the manifest describes a Pod resource and determines which resource specification Kubernetes should apply.

## 1. Set Resource Kind

Specifies the type of Kubernetes resource being defined in the manifest. The kind field tells Kubernetes what the object represents, such as a Pod, Deployment, or Service, so it knows which resource configuration and behaviour to apply.

    ## Prints text to the terminal — also used to write to files with > or >>.
    echo "kind: Pod" >> pod.yaml

<img width="704" height="184" alt="2026-08-12_10h30_44" src="https://github.com/user-attachments/assets/74214db0-80c0-4525-bcb9-e43ce0958701" />
    
## Nesting Data (Metadata)

Creates a nested **_metadata_** object and assigns the resource name as **_nginx-pod_**. The **_metadata_** section stores identifying information about the Kubernetes resource, such as its name, labels, and annotations, allowing Kubernetes and users to uniquely identify and manage the Pod.

## 1. Add Metadata Key

Defines the parent **_metadata_** key to create a structured section for the Pod's identifying information. **_YAML_** uses indentation and nesting to group related properties together, making Kubernetes manifests easier to read, organize, and maintain.

    ## Prints text to the terminal — also used to write to files with > or >>.
    echo "metadata:" >> pod.yaml

<img width="710" height="195" alt="2026-08-12_10h31_47" src="https://github.com/user-attachments/assets/85f24ffb-49c0-4e63-975b-778252ee255d" />

## 2. Add Nested Name

YAML uses indentation with spaces, not tabs, to represent hierarchical relationships between data. The **_name_** field is indented two spaces under **_metadata_**, indicating that it belongs to the **_metadata_** object. In Kubernetes, metadata provides essential information for identifying, organizing, and managing resources, including names, labels, and annotations.

    ## Prints text to the terminal — also used to write to files with > or >>.
    echo "  name: nginx-pod" >> pod.yaml

<img width="704" height="226" alt="2026-08-12_10h32_52" src="https://github.com/user-attachments/assets/dd1f6d3f-e7c4-41cd-838d-ffb4dfa3cf96" />

## Lists and Arrays (Containers)

Defines the containers field as a YAML sequence (list) and adds a container named **_nginx_**. Kubernetes uses this list to specify the containers that should run inside the Pod, with each container defined as an individual object containing its own configuration, such as the image, ports, environment variables, and resource settings.

## 1. Add Spec Key

Defines the **_spec_** block, which contains the desired state and configuration of the Kubernetes Pod. It separates the resource's metadata and identification details from its operational configuration, such as containers, images, ports, environment variables, and resource requirements.

    ## Prints text to the terminal — also used to write to files with > or >>.
    echo "spec:" >> pod.yaml

<img width="706" height="240" alt="2026-08-12_10h34_03" src="https://github.com/user-attachments/assets/3269bf74-7ba8-4e82-bd23-ae485a101764" />

## 2. Add Containers Array

Defines the **_containers_** field as a YAML sequence (list) within the Pod's **_spec_**. Kubernetes uses a list because a Pod can contain one or more containers, with each container represented as an individual object containing its own configuration, such as the container name, image, ports, and environment variables.

    ## Prints text to the terminal — also used to write to files with > or >>.
    echo "  containers:" >> pod.yaml

<img width="704" height="264" alt="2026-08-12_10h39_24" src="https://github.com/user-attachments/assets/c11e34a7-a542-48b7-942a-1c9c93a90567" />

## 3. Add First Container Item

The hyphen **(-)** identifies an item in a YAML sequence (list) and marks the beginning of the first **_container_** definition within the containers list. Each list item can contain multiple key-value pairs that define the container's configuration, such as its name, image, ports, and environment variables.

    ## Prints text to the terminal — also used to write to files with > or >>.
    echo "  - name: nginx" >> pod.yaml

<img width="709" height="263" alt="2026-08-12_10h40_11" src="https://github.com/user-attachments/assets/c3f3e02a-9a49-4e5c-993f-44195de8a766" />

## Completing the Pod

Adds the **_image_** field to the container definition to specify the container image Kubernetes should use when creating the container. The image identifies the application and its required runtime environment, such as **_nginx:latest_**, that will be pulled from a container registry.

## 1. Set Container Image

Adds **_image: nginx:latest_** to the **_pod.yaml_** file to specify the container image Kubernetes should pull and run. The **_image_** field must be indented four spaces, aligning with the **_name_** field, to show that both properties belong to the same container object. Using **>>** with **_echo_** appends the new configuration line to the existing file without overwriting its contents. Explicitly defining the container image ensures Kubernetes knows exactly which application image to deploy.

<img width="737" height="265" alt="2026-08-12_10h51_32" src="https://github.com/user-attachments/assets/ef59ff7b-5704-440b-864c-2db6dafc1dbe" />

## Deploy to GitHub

Review the Kubernetes YAML manifest for correctness, stage the changes with Git, create a commit with a clear message, and push the updated repository to GitHub. This workflow ensures configuration changes are validated, version-controlled, and safely stored in a remote repository.

## 1. View Your Complete Manifest

Displays the complete **_pod.yaml_** file to verify that all Kubernetes configuration fields, indentation, and nested structures are correctly defined. Reviewing the manifest before committing helps identify syntax, formatting, and configuration errors early, reducing the risk of deployment failures and ensuring only validated changes are stored in version control.

    ## Displays the contents of a file in the terminal.
    cat pod.yaml

<img width="836" height="298" alt="2026-08-12_10h52_26" src="https://github.com/user-attachments/assets/5b697cff-cf70-4479-8592-79cfb8e30f13" />

## Stage All Changes

    git add .

## Commit Your Manifest

    git commit -m "feat: create nginx pod YAML manifest"

## Add GitHub Remote

    git remote add origin https://github.com/YOUR_USERNAME/kubernetes-Yaml-Achitecture.git

## Rename to Main Branch

    git branch -M main

## Push to GitHub

    git push -u origin main

<img width="835" height="381" alt="2026-08-12_10h56_13" src="https://github.com/user-attachments/assets/66b5f91d-0d1a-422b-9aab-5643858ee413" />

## Conclusion

The project demonstrates a complete workflow for creating, structuring, validating, and version-controlling a Kubernetes YAML manifest.

Starting with a minimal configuration, the manifest is progressively built into a Pod definition containing metadata and a container specification. The completed configuration is then committed to Git and pushed to GitHub, providing a structured, traceable, and maintainable representation of the Kubernetes infrastructure configuration.
    
