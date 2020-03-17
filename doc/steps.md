### Basic steps to follow

1. **Create the directory**

    ```bash
    mkdir services
    ```

2. **Create the bootstrap file**

    create the create-projects.bash in this folder, and generate the skeleton of the project. This will create the 4 microservices for us
    * product service
    * review service
    * recommendaetion service
    * product composite service, which is depending on the 3 core services

3. **Create build file for the project**
    
    Now we want to build our project instead of build each service one by one, we make one multi-project build for for our project. create one settings.gradle in our <ROOT_PROJECT>, and add these content

    ```bash
    include ':microservices:product-service'
    include ':microservices:review-service'
    include ':microservices:recommendation-service'
    include ':microservices:product-composite-service'
    ``` 
4. **Add necessary files for root project**

    So we need some gradle realated files for the whole project. We can simply copy from we just generated. 
    
    ```bash
    cp -r microservices/product-service/gradle .
    cp microservices/product-service/gradlew .
    cp microservices/product-service/gradlew .
    cp microservices/product-service/.gitignore .
    ```
5. **remove the the gradle executable files we no longer need**
    ```bash
    find microservices -depth -name "gradle" -exec rm -rfv "{}" \; 
    find microservices -depth -name "gradlew*" -exec rm -fv "{}" \; 
    ```
6. **Try to build**
    ```bash
    ./gradlew build
    ```

