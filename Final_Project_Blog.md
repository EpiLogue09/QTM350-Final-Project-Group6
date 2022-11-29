#Evaluating the Accuracy of Amazon Textract - Handwritten vs Typed

Group #6: Ruishi Chen, Vivienne Yu, Joyce Wang, Eric Yang, Mark Si

##Introducing our team

#### Member 1: Ruishi Chen
>![picture](https://drive.google.com/uc?export=view&id=1Sdu7ayw28J4ubTPoNF_cJmzavrtwGuf4)

>*Hometown:* Chonqging

>*Year:* Junior

>*Majors:* Applied Mathematics and Statistics + Sociology 

>*Interests:* Workout and Hike 

#### Member 2: Yicheng(Eric) Yang 
>![picture](https://drive.google.com/uc?export=view&id=1oC_7N1V8HNIYQzAWgppWQYZSWfzOCV_S)
>*Hometown:* Suzhou 

>*Year:* Junior

>*Major/Minor(s):* 
Applide Mathematics and Statistics + Computer Science

>*Interests:* Magic Trick 

#### Member 3: Mark Si
>![picture](https://drive.google.com/uc?export=view&id=1If8-Vfl2aW_ewU4tG88sP3lw9R3jJE2N)
>*Hometown:* Shenzhen

>*Year:* Junior

>*Majors:* Philosophy + Quantitative Science with Informatics 

>*Interests:* Metal 

#### Member 5: Joyce Wang 
>![picture](https://drive.google.com/uc?export=view&id=1umy38-B56AzMCLMK4UfdkZC8FWQGve0W)

>*Hometown:* Hangzhou

>*Year:* Senior

>*Majors:* Quantitative Science + Psychology 

>*Interests:* Travel

#### Member 6: Vivienne Yu 
>![picture](https://drive.google.com/uc?export=view&id=1NY4GMtyjvpWXiUWJgqNCqCGx-V8R7ZsI)
>*Hometown:* Beijing 

>*Year:* Senior

>*Majors:* Applied Mathematics and Statistics + Film and Media Studies 

>*Interests:* Watching Movies

## Project Introduction

###Why Amazon Textract?
Taking a map photo with my newest iPhone 12 while going to Legoland in San Diego, I realized that my phone can automatically detect the text in the photo, and I can easily extract the text and paste it in the text form. After finding out this cool ability that my phone can do, I start taking pictures of the handouts from my classes, and easily convert the paper-copy into a text file into my laptop. Ever since I start using this “super-ability,” my backpack is forever lighter.

As a person who prefers taking notes with a pen and paper, I thought this might also help converting my notes into a digital version. However, when I scribble my notes under a very short period of time, my phone fails to detect the words correctly and it would not improve my efficiency for a greater extend. I want to find a tool that might satisfy this need. With that in mind, my team and I choose Amazon Textract, a very useful and powerful machine learning (ML) service from AWS, that could be an essential tool for natural language processing or any kinds of language processing machine learning algorithm. 

Since the majority of our team members doubled majored in a stem major together with a social science/humanity major, we are interested in some sort of interdisciplinary study that utilizes both computer science and a different area of study. Therefore, besides running Textract on the modern language, we also select “old” language, Shakespeare, and math equations to run on Textract. Because we usually hand-write math equations, it would be very efficient if we can get the hand-written math equations converted into digital version under the time of just taking a picture. Additionally, many old literatures have only copies in the library, it would also be beneficial if we can convert the physical literature into a digital version where we can highlight on the electronic device instead of damaging the precious old copies. We have two sample groups, one hand-written, one typed, and we want to check the accuracy for both after running them on Textract. Hopefully, evaluating the accuracy for Amazon Textract can also facilitate our research in other areas in the future.

###What is Amazon Textract?

>![picture](https://drive.google.com/uc?export=view&id=1WONCX5ouLURhg0lg2fnpEnIGq6CUjNqu)

Amazon Textract is a machine learning (ML) service that automatically detect typed and handwritten text, extract text, forms, and tables with structured data, specify and extract information, process invoices and receipts, and process ID documents, in application.

People usually utilize Amazon Textract in the following case:

- Creating an intelligent search index

- Using intelligent text extraction for natural language processing (NLP)

- Accelerating the capture and normalization of data from different sources

- Automating data capture from forms

The benefits of using Amazon Textract includes:

- Integration of document text detection into your apps

- Scalable document analysis

- Low cost

###Research Question

Due to Amazon Textract's ability to extract different types of text, we especailly want to focus on **how accurate is its ability to detect and extract text blocks for handwritten text vs typed text**. 

###Hypothesis

We first expect the printed version should have higher accuracy than the hand-written version. Secondly, we expect the modern language would be the easiest to detect, following the old language, then the math equations.

##Experiment Design

### Research Methods

We are going to create a few sample text blocks containing different types of information and English styles, and for each sample text blocks there will be a typed version and a handwritten version. For the typed version, we will have a screenshot of the typed text block. For the handwritten version, we will have a picture of the handwritten text block. 

Next, all the pictures containing the text blocks will be uploaded to the S3 bucket. We will, then, use Amazon Textract to detect and process the pictures uploaded for the text blocks contained in them. 

Finally, we will format the returned text to show type, the detected text, the percentage for confidence(the higher the percentage the higher the confidence in detecting the correct text), and the uploaded images with bounded lines showing what is being extracted from the image.

To check the accuracy, we will calculate the percentage for the words correctly extracted for both the handwritten text and the typed text and compare the results.


### Data Collection

The most important part of our experiment is to choose the. In order to see how accurately Amazon Textract pull out the words, we are going to use printed words and hand written words to compare and contrast the result. Four types of words are used:

- Modern English
>![picture](https://drive.google.com/uc?export=view&id=1Dv19HsX0WJd7SzBWW7CHMg8gI2ph4Yzw)
>![picture](https://drive.google.com/uc?export=view&id=1huMfr5N0_Rnni-ebdhcRuxS2zXTi2s8u)
- Shakespeare so called “old English”
>![picture](https://drive.google.com/uc?export=view&id=1dQVq7AJOHy1bBeHgGlEvHO6GeYwneqkb)
>![picture](https://drive.google.com/uc?export=view&id=1f_vHvrbXBZuLRjrCXj8fiOLKRz1Xildv)
- Number with math characters
>![picture](https://drive.google.com/uc?export=view&id=13yft7eMcJwAykRu1HiGnkeppvhEZN1dn) 
>![picture](https://drive.google.com/uc?export=view&id=1GM-ULiJgnhRuYvg6WiehTTJ8hXhwBREZ)
- Random scribble that are not a language
>![picture](https://drive.google.com/uc?export=view&id=1LbDdoKb-XbHvsLtj3m50yQi5-0BcUwa8)

One of our members is going to type and write all the texts to control the variations in handwriting styles. 


### Architectural Diagram

>![picture](https://drive.google.com/uc?export=view&id=1cXPCMGR2iPSejPMe16YUciKbVOYQc-Qx)

**Architecture of Amazon Textract**

The architecture diagram shows the specific steps of the architecture. Since we are using the AWS Textract service in a SageMaker Notebook, the first component of our processing architecture is to initiate an Amazon SageMaker notebook instance in the specifically available elastic compute cloud regions through Amazon SageMaker (Step (1) —> (2)). We use Jupyter Lab notebook to build our pipelines for the implementation. In the meanwhile, we uploaded the files we wish to process to the S3 bucket (3). By calling the bucket in the SageMaker notebook (4), we were able to obtain the images and pass them to the Textract APIs (5). After we obtain the outputs from the Textract in the SageMaker notebook (6), we added our GitHub repository to the Amazon SageMaker and pushed our notebook to the repo (7). More official guidance on the steps is listed below.

1. ~ 2. The user initiates the Amazon SageMaker notebook instance in the allowed regions.
3. User uploads images, and text files to Amazon S3 bucket.
4. Amazon SageMaker calls the S3 bucket to obtain the files for processing (as the user command in the notebook through pipelines). 
5. User uses Textract APIs to scanned and analyzed the uploaded files. 
6. Amazon Textract outputs its result in the notebook.
7. User pushes the notebook to the GitHub repo that was added in the SageMaker.

**Potential implementation of the study result**

Our study’s results will help its audiences to distinguish the materials that are most suitable for Amazon Textract service and the accuracy of processing their desired file types. Subsequently, by knowing the accuracy of Textract, the users of Textract can make a better selection when choosing text analysis services and become aware of potential errors the ML service may produce. 

## Walkthrough

### Step 1:
#### We Need to Import the Corresponding Packages

Because we want to use Python SDK, or integrating Python application, library or script with AWS services (like S3 and Textract), we need to import **boto3**. 

Also, since Textract mainly deals with Image, or trying to help us extract information from image, we need the **Image** and **ImageDraw** module from Pillow to help us to import our data using pictures, retouch existing images, and generate new image after it is processed by the service. 

Last but not lease, we need to use **io** to help us read information from whatever file we choose to use.


```python
import boto3
import io
from PIL import Image, ImageDraw
```

### Step 2: 
#### Import the file we want to process to the S3 bucket. 

First of all, we need to know what buckets do we have using the ls:




```python
!aws s3 ls
```

In there, we could see that our group have created a S3 bucket specifically for this final project. So, this is the bucket where we want to use to import the file that is ready to be processed. In general, you could just choose a bucket to use for the purpos of using the service. 

Then, we could upload the image we want to process using the AWS service into this notebook. After upload, we could check if we have successfully done so using *ls*


```python
!ls
```

After we upload and before we move our image to the busket we are going to use, it shoudl show the image file with this ipynb notebook.

Next, we could move the image to the S3 bucket using the following code: 

*!aws s3 mv IMAGE_NAME s3://BUCKET_NAME*

Where the capitalized part within this code needs to be changed into your corresponding information. Take our groups' image and bucket as an example: 


```python
! aws s3 mv Emory-website.png s3://finalproject-group5
```

We could double check if the file is in the bucket we want to import our file to process using *ls*: 


```python
!aws s3 ls finalproject-group5
```

As shown above, the file is already there. So now we are ready to use our service to process the image. 

### Step 3: 
#### Start using AWS Serviec to Extract Information from Image

Firstly, we need to use the *boto3* to connect with our *s3* bucket. Then, we need to find the specific object from the bucket and make the connection so we get the resource ready for the service to run through. 

When making the connection we could just use the following code: 

*s3_connection.Object("BUCKET NAME","IMAGE NAME")*

Again, where the capitalized part within this code needs to be changed into your corresponding information.

s3_connection = boto3.resource('s3')
                          
s3_object = s3_connection.Object("finalproject-group5","Emory-website.png")
s3_response = s3_object.get()

Next, we need to read the resource we get from the s3 bucket. 


```python
stream = io.BytesIO(s3_response['Body'].read())
image=Image.open(stream)
```

Now, it's time for us to call the service our and prepare for the service to run through our file. 

In general, to call service using Python SDK, we could use: 

*boto3.client('SERVICE NAME')*

(where the capitalized part within this code needs to be changed into your corresponding information)


```python
client = boto3.client('textract')
```

To use this ervice, we could use the following code to tell the computer all the information it needs to find the file it will run service through:

*response = client.detect_document_text(Document={'S3Object': {'Bucket': "BUCKET NAME", 'Name': "IMAGE NAME"}})*

(S30bject -- is the resource where you make connection from previous codes.)


```python
response = client.detect_document_text(
    Document={'S3Object': {'Bucket': "finalproject-group5", 'Name': "Emory-website.png"}})
```

Then, we want to show our response as blocks so it is easy to see what is detected and what is not. Also, we want to create the printed notification to notify if the service is successfully run through. 


```python
blocks=response['Blocks']
width, height =image.size    
print ('Detected Document Text')
```

Lastly, we could just show what it is detected from calling our named object *blocks*


```python
blocks
```

## Experiment Process

For the three types of text mentioned above (modern English, Old English, and math), we respectively conduct two experiments within each category to examine the accuracy of the Amazon Textract. The two experiments are as followed: 
1. Handwritten analysis: one of our group member writes the text out on a sheet of paper, and we examine how accurate can the Amazon Textract identify these handwritings;
2. Typed analysis: Instead of writing with hands, one of our group member types the text out and takes a screenshot for the Amazon Textract to identify the sentences.

### 1. Analysis of Modern English

####Handwritten Analysis:

Text:
>![picture](https://drive.google.com/uc?export=view&id=1huMfr5N0_Rnni-ebdhcRuxS2zXTi2s8u)

Output of Amazon Text Extract:
>![picture](https://drive.google.com/uc?export=view&id=1rNmJeseVShGuvsI7EWu6eWiAy986qWml)
>![picture](https://drive.google.com/uc?export=view&id=14vyrrdYxiyPBEfpLF_CchW_ms3t9ADiX)

From above, we can see that the Amazon Textract has a 79/84 = 94% accuracy when examining the handwritten modern english text (incorrect extractions are marked by the red circle). During the writing process, our member deliberately makes certain letters continuous and italicized, checking if the text extract algorithm would identify these letters. Surprisingly, as shown in the blue circles, these letters are accurately identified by the algorithm, and we are very impressed by this accuracy rate.

####Typed Analysis

Text:
>![picture](https://drive.google.com/uc?export=view&id=1HTyBAFVUIkKiZWL9_6C_-kbcMwy04K3z)

Output of Amazon Text Extract:
>![picture](https://drive.google.com/uc?export=view&id=1MxrW5kEJgIrBiEYi88w5rXyExp5EeTnl)

From above, we can see that the Amazon Textract has a 100% accuracy when it is dealing with typed modern English text. Though expected by many of our group members, this is nevertheless a very impressive result. We can also see that the algorithm always has a more than 99.5% confidence when analyzing the typed text, meaning this accuracy rate is not likely achieved by chance.

### 2. Analysis of "Old English"

####Handwritten Analysis:

Text:
>![picture](https://drive.google.com/uc?export=view&id=1HjZzf1dEzqnYOmv6Sg3jSZbxtSktAWi-)

Output of Amazon Text Extract:
>![picture](https://drive.google.com/uc?export=view&id=16kPYHFNppFIZKHUPvdIUGgPQPmO16d5f)
>![picture](https://drive.google.com/uc?export=view&id=1vSAdxVNBvtPv9y8nez1AtY8VZvcUcQf8)

From above, we can see that the Amazon Textract has a 53/55 = 96.36% accuracy when examining the handwritten "old english" text (incorrect extractions are marked by the red circle). Surprisingly, considering the amount of scribbles and cursive letters in the handwritten text, the Amazon Textract has a even better performance when analyzing "old english" text.

####Typed Analysis:

Text:
>![picture](https://drive.google.com/uc?export=view&id=1FZHnEzT1dFVqGlJGKN0eD2UovwM_dMVu)

Output of Amazon Text Extract:
>![picture](https://drive.google.com/uc?export=view&id=133r_0DMmHbnnXDGWaWPdlgA2pu4ojYpt)
>![picture](https://drive.google.com/uc?export=view&id=1m-CwCyALreTZKcGzHKU8phOo5hsFPoJB)

From above, the Amazon Textract has a 100% accuracy when examining the typed "old english" text. This result is consistent when considering the Amazon Textract's perfect result with the modern english text. From the observations above, we can arrive at a preliminary hypothesis here, that the Amazon Textract has no preference over either modern or old english text, no matter handwritten or typed.

### 3. Analysis of Math Languages and Numbers

####Handwritten Analysis:

Text:
>![picture](https://drive.google.com/uc?export=view&id=1u_z1qMWwKLFsKu7I4LKyEqykGLsFVFZo)

Output of Amazon Text Extract:
>![picture](https://drive.google.com/uc?export=view&id=1M9DmraUJj7C2Bc5PMPVsm9yYBq0FgkZn)
>![picture](https://drive.google.com/uc?export=view&id=1tq-BaqL4m50wJ2ArEYtZRF9GcJnmr6zZ)

From above, we can see that the Amazon Textract has a 59/72 = 81.94%
accuracy when examining the handwritten math language text (incorrect extractions are marked by the red circle). This result is significantly lower than the previous two cases, and we believe that several things are happening here: first, the Textract algorithm fails to detect the cursive letter 'I' and treat it as a 'Z' (which is a closer match graphical wise, if not considering the context); second, the text extract algorithm is unable to detect the power letter we put in the text, and in all cases, it transforms the second power to either a plain '2' or a letter 'z'.

####Typed Analysis:

Text:
>![picture](https://drive.google.com/uc?export=view&id=1knRMPdqvX1WGyOT3OuFg5dWYUJ_L733m)

Output of Amazon Text Extract:
>![picture](https://drive.google.com/uc?export=view&id=1mqS8_8jhdwPE98aMbMPMB7D-SGah0qQ2)


Once again, we obtain a result of 100% accuracy with the typed text. The problem with the cursive letters, as shown in the handwritten case, is no longer a issue here, as every letter is standardized and easily recognizable. We are able to conclude that the Amazon Textract has a incredible, if not perfect, performance towards the typed text, no matter what the content is. 

## Results and Conclusion

Here is the result for Modern English:

The handwritten version:

>![picture](https://drive.google.com/uc?export=view&id=1eGPlOtr1QeuXelzePGUOdRxiEl6r2Anp)

>![picture](https://drive.google.com/uc?export=view&id=1ROmMpuzDskcFteRBF0shKme38jMYkMQz)

>![picture](https://drive.google.com/uc?export=view&id=1eng737mlpLCZHEPHuz9bJIfZ3TLe5q1b)

94% of the detected words are correct for the handwritten version.

The typed version:

>![picture](https://drive.google.com/uc?export=view&id=1jSbx1oazRuTAcMlC2SY6OTU_Ge92DXLS)


This is what is run out for the printed words. The confidence levels are extremely high as expected.


Here is the result for Old English:

The handwritten version:

>![picture](https://drive.google.com/uc?export=view&id=172QT-Oa2m0z7BIlNfWrAQE42HAJQ1eHj)

>![picture](https://drive.google.com/uc?export=view&id=1bs3BWErbp7ZzEjv6RRsIF5KeXFwQUrpv)

>![picture](https://drive.google.com/uc?export=view&id=1s0PCSmuaVdbdtCxGjUfySmjddWo1fzcz)

96.36% of the detected words are correct for handwritten version.

The typed version:

>![picture](https://drive.google.com/uc?export=view&id=1iJCu8J9lqQBsr9lL8qoSNnXXlHxUPzqP)

>![picture](https://drive.google.com/uc?export=view&id=1KP_VwDCF1mLbgsGRoTvTBL5s2HNavcTb)

All correct; the confidence level is nearly perfect 100%.



Here is the result for math language:

The handwritten version:

>![picture](https://drive.google.com/uc?export=view&id=1S2RzkMhqHtspaI_1O4UFFy3Gvgcpq7Uf)

>![picture](https://drive.google.com/uc?export=view&id=12JQSyp9OgexrdKf0120BVh4Oo7G-QDWZ)

>![picture](https://drive.google.com/uc?export=view&id=1C64bNi551I0gVL7heHU2YAbfoPxS_tPZ)

81.94% of the detected words are correct for the handwritten version.

The typed version:

>![picture](https://drive.google.com/uc?export=view&id=1nAGyHVVwzOGLoxkbiES0GmFfT3ayckGh)

All correct; the confidence level is nearly perfect 100%.

Based on our data and analysis, for the first hypothesis, the evidence supports that Amazon Textract will have a better accuracy in detecting information from typed text than hand-written text. 

Then, for the second hypothesis, Textract does a better job in detecting modern language and “old English” than Math. And this is because Textract has difficulty in identifying upper subscript and lower subscript in mathematical operations. In addition, when we only have a capitalized letter independently standing in a line for operation, Textract has high rate of false identification. 

As a result, our data helped us test our hypothesis, showing the strength and the weakness of Textract as an ML Service.
