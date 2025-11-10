# Host a Website on Amazon S3

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-host-a-website-on-s3)

**Author:** gokulnath anand  
**Email:** gokulnathanand23@gmail.com

---

![Image](http://learn.nextwork.org/relieved_turquoise_lucky_matata/uploads/aws-host-a-website-on-s3_5d4474f9)

---

## Introducing Today's Project!

In this project, I will demonstrate the process of hosting a website on Amazon S3. The objective of this project is to gain practical knowledge of the Amazon S3 service and to learn how to host a website on Amazon S3 by uploading website content into S3 and subsequently making it publicly accessible.

### Tools and concepts

Services I used were Amazon S3 for storing and hosting my website files. Key concepts I learnt include how to create an S3 bucket, upload and manage objects, enable static website hosting, set file permissions using ACLs, and understand how website hosting makes files publicly accessible on the internet.


### Project reflection

It took me about 30 to 45 minutes to complete this project, including creating the S3 bucket, uploading the files, configuring static website hosting, and troubleshooting the 403 error.


---

## How I Set Up an S3 Bucket

Creating an S3 bucket took me around 5–10 seconds.

I chose the US East (N. Virginia) – us-east-1 region for my S3 bucket because it offers low latency, high availability, and is one of the most cost-effective regions. It’s also the default region for many AWS services, which makes integration and testing easier. Additionally, since most of my users and applications are based in the eastern U.S., hosting data in that region helps minimize latency and improve performance.

When we say that Amazon S3 buckets must be globally unique, it means that no two S3 buckets anywhere in the world can have the same name.

This is because each bucket name forms part of a unique URL for accessing the bucket (for example: https://my-bucket-name.s3.amazonaws.com).
Since these URLs are accessible over the global internet, AWS needs each bucket name to be unique across all AWS accounts and all regions, not just within your own account or region.

![Image](http://learn.nextwork.org/relieved_turquoise_lucky_matata/uploads/aws-host-a-website-on-s3_ba6d42ad)

---

## Upload Website Files to S3

### index.html and image assets

I uploaded two files to my S3 bucket - they were my index.html file and the unzipped folder into my S3 bucket so I can host my static website on AWS.

Both files are necessary for this project as the index.html file is the main webpage, and the unzipped folder contains all the supporting files—like images, styles, and scripts—that the HTML file needs to display the website correctly.


![Image](http://learn.nextwork.org/relieved_turquoise_lucky_matata/uploads/aws-host-a-website-on-s3_a265af88)

---

## Static Website Hosting on S3

Website hosting what makes your website public on the internet.

Even if you perfect an HTML file, no one else can see it when it's stored as a local file on your computer! Website hosting = storing your HTML file (and the other files for your website) on a web server, so it's accessible online.

By configuring your S3 bucket for hosting, we're telling this bucket: "please create a URL that will take anyone to a page that displays the HTML file I just uploaded."

To enable website hosting with my S3 bucket, I went to the Properties tab, scrolled to Static website hosting, chose Edit, then enabled static website hosting, selected Host a static website, and entered index.html as the index document.


ACL stands for Access Control List. It’s like a set of rules that decides who can access a resource in your s3 bucket. You can either turn it on or off, but I’ve turned it on for this project to show you how it works.

![Image](http://learn.nextwork.org/relieved_turquoise_lucky_matata/uploads/aws-host-a-website-on-s3_c22c54c0)

---

## Bucket Endpoints

Once static website is enabled, S3 produces a bucket endpoint URL, which is http://nextwork-website-project-gokulnath.s3-website-us-east-1.amazonaws.com

When I first visited the bucket endpoint URL, I saw 403 Forbidden error. The reason for this error was because my Objects (in this case, the HTML and images files you uploaded) are private by default. This default setting helps keep your account's data secure.

The error message you're seeing is telling you that your static website is being hosted by S3, but the actual HTML/image files you've uploaded are still private. It's kind of like having a bucket on display, so everyone can see the bucket - but the contents are covered up, preventing anyone from seeing what's inside.

![Image](http://learn.nextwork.org/relieved_turquoise_lucky_matata/uploads/aws-host-a-website-on-s3_22ce4daf)

---

## Success!

To resolve this 403 Forbidden error, I made my S3 bucket objects public by going to the Objects tab, selecting the checkboxes next to my index.html file and asset folder, choosing Actions, then Make public using ACL, and confirming the changes. After that, I refreshed the page to view my website.


![Image](http://learn.nextwork.org/relieved_turquoise_lucky_matata/uploads/aws-host-a-website-on-s3_5d4474f9)

---

## Bucket Policies

An alternative to ACLs are bucket policies, which are JSON-based permissions that let you control access to your entire S3 bucket or specific objects. The benefit of using bucket policies is that they provide more flexibility and fine-grained control over actions like deleting, uploading, or viewing objects, while ACLs are useful for quickly setting simple public or private access permissions.


My bucket policy denies everyone permission to delete the index.html file in my S3 bucket. I tested this by trying to delete the file, and saw an “Access Denied” error message, confirming that the policy successfully blocked the deletion.


![Image](http://learn.nextwork.org/relieved_turquoise_lucky_matata/uploads/aws-host-a-website-on-s3_sm2sm2sm)

---

---
