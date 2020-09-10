# LAB: Getting Started with Compute Engine

## Objectives
In this lab, you will learn how to perform the following tasks:

    1. Create a Compute Engine virtual machine using the Google Cloud Platform (GCP) Console.

    2. Create a Compute Engine virtual machine using the gcloud command-line interface.

    3. Connect between the two instances.

## Task1: Authentication

Sign in to the Google Cloud Platform

## Task2: Create a virtual machine using the GCP Console

### Steps:

1. Create a virtual machine using the GCP Console

   * gcloud compute instances create my-vm-1 --machine-type 'n1-standard-1' --image-project 'debian-cloud' --image 'debian-9-stretch-v20190213' --subnet 'default' --tags http 

## Tasks3: Create a virtual machine using the gcloud command line

### Steps:

<b>1</b>. Display a list of all the zones in a region

   * gcloud compute zones list | grep us-central1

<b>2</b>. Set the Zone to us-central1-b

   * gcloud config set compute/zones us-central1-b

<b>3</b>. Create the second instance

   * gcloud compute instances create my-vm-2 --machine-type 'n1-standard-1' --image-project 'debian-cloud' --image 'debian-9-stretch-v20190213' --subnet 'default'

## Tasks4: gcloud compute zones list | grep us-central1

### Steps:

<b>1</b>. <i>SSH</i> into my-vm-2

   * gcloud compute ssh my-vm-2 

<b>2</b>. Use the <i>ping</i> command to confirm that my-vm-2 can reach my-vm-1 over the network

   * ping -c 3 my-vm-1

<b>3</b>. Use the <i>ssh</i> command to open a command prompt on my-vm-1

   * ssh my-vm-1

<b>4</b>. At the command prompt on my-vm-1, install the Nginx web server

   * sudo apt-get install nginx-light -y

<b>5</b>. Use the <i>nano</i> text editor to add a custom message to the home page of the web server

   * sudo nano /var/www/html/index.nginx-debian.html

<b>6</b>. Use the arrow keys to move the cursor to the line just below the h1 header. Add text like this, and replace <i>YOUR_NAME</i> with your name

   * Hi from YOUR_NAME

<b>7</b>. Press Ctrl+O and then press Enter to save your edited file, and then press Ctrl+X to exit the <i>nano<i> text editor

<b>8</b>. Confirm that the web server is serving your new page. At the command prompt on my-vm-1, execute this command

   * curl http://localhost/

         Result: The response will be the HTML source of the web server's home page, including your line of custom text

<b>9</b>. To exit the command prompt on my-vm-1, execute this command

   * exit

<b>10</b>. To confirm that my-vm-2 can reach the web server on my-vm-1, at the command prompt on my-vm-2, execute this command

    * curl http://my-vm-1/

          Result: The response will again be the HTML source of the web server's home page, including your line of custom text

<b>11</b>. Copy the <i>External IP address</i> for my-vm-1 and paste it into the address bar of a new browser tab. You will see your web server's home page, including your custom text

    * gcloud compute instances list --zone us-central1-b
