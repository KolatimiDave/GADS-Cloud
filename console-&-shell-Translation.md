# LAB: Console and Cloud Shell

## Objectives

In this lab, you learn how to perform the following tasks:

	1. Get access to Google Cloud.

	2. Create a Cloud Storage bucket using the Cloud Console.

	3. Create a Cloud Storage bucket using Cloud Shell.

	4. Become familiar with Cloud Shell features.

Sign in to the Google Cloud Platform

## Task1: Create a bucket using the Cloud Console

1. In the Cloud Console, on the Navigation menu, click Storage > Browser.

   * gsutil mb 'GLOBALLY-UNIQUE-NAME'

## Task 2: Create a bucket using Cloud Shell
1. For convenience, place the bucket name you choose into an environment variable called BUCKET_NAME. At the Cloud Shell prompt, type this partial command

   * export BUCKET_NAME=

      followed by the bucket name you'll be using. your completed command will look similar to this

      * export BUCKET_NAME=spaceX-Restaurant

2. Use the gsutil command to create another bucket. Replace <BUCKET_NAME> with a globally unique name (you can append a 2 to the globally unique bucket name you used previously)

   * gsutil mb gs://$BUCKET_NAME

## Task 3: Explore more Cloud Shell features

1. Since you're working from your local computer, choose a file you want to upload into one of your cloud storage buckets.

   * gsutil cp 'sample.txt' gs://$BUCKET_NAME


## Task 4: Create a persistent state in Cloud Shell

### Steps:

1. To list available regions, execute the following command:

   * gcloud compute regions list

2. Select a region from the list and note the value in any text editor. This region will now be referred to as [YOUR_REGION] in the remainder of the lab

   * export INFRACLASS_REGION=

     followed by the region you'll be using. your completed command will look similar to this
	
     * export INFRACLASS_REGION=[YOUR_REGION]

3. Verify it with echo:

   * echo $INFRACLASS_REGION

#### Append the environment variable to a file


1. Create a subdirectory for materials used in this class

   * mkdir infraclass

2. Create a file called config in the infraclass directory:

   * touch infraclass/config

3. Append the value of your Region environment variable to the config file:

   * echo INFRACLASS_REGION=$INFRACLASS_REGION >> ~/infraclass/config

4. Create a second environment variable for your Project ID, replacing [YOUR_PROJECT_ID] with your Project ID. You can find the project ID on the Cloud Console Home page.

   * export INFRACLASS_PROJECT_ID=[YOUR_PROJECT_ID]

5. Append the value of your Project ID environment variable to the config file:

   * echo INFRACLASS_PROJECT_ID=$INFRACLASS_PROJECT_ID >> ~/infraclass/config

6. Use the source command to set the environment variables, and use the echo command to verify that the project variable was set

   * source infraclass/config
   * echo $INFRACLASS_PROJECT_ID  

7. Close and re-open Cloud Shell. Then issue the echo command again:

   * echo $INFRACLASS_PROJECT_ID

     There will be no output because the environment variable no longer exists.

#### Modify the bash profile and create persistence

1. Edit the shell profile with the following command:

    * nano .profile

2. Add the following line to the end of the file:

   * source infraclass/config

3. Press Ctrl+O, ENTER to save the file, and then press Ctrl+X to exit nano.

4. Close and then re-open Cloud Shell to cycle the VM.

5. Use the echo command to verify that the variable is still set:

   * echo $INFRACLASS_PROJECT_ID

	
