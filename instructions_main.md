---
layout: default
title: Update Instructions
#has_children: true
#parent: ISOM Playbook
#nav_order: 2
nav_exclude: true
---

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Site Update Instructions
{: .no_toc}

Please use below instructions to update the code which will reflect back on the site immediately.


Note: Any updates to pages must be committed to "gh-pages" branch in order to reflect on website. If you are forking a branch, remember to push updates to "gh-pages" branch
{: .fs-4 .text-red-300}
<br />

**DO NOT Commit to "master" branch**
{: .fs-4 .text-red-300}


### Folder Structure

This website is following the below mentioned folder structure

````markdown

-/ (mentioned as root in below examples)

Subfolders are created inside root

-root/folder1/

Images or any other data pertaining to that subfolder should be kept inside subfolder

-root/folder1/img/

````



Following folders have been created for respective streams



| Folder Name              | Purpose                                                           | 
|:-------------------------|:------------------------------------------------------------------|
| hmcp                     | Hybrid Multi Cloud Platform documentation                         | 
| hmcp/img                 | Hybrid Cloud Service Management Operations images                 | 
| hcsmo                    | Hybrid Cloud Service Management Operations documentation          | 
| hcsmo/img                | Hybrid Cloud Service Management Operations images                 | 
| devsecops                | DevSecOps stream documentation                                    |
| devsecops/img            | DevSecOps stream  images                                          | 
| observability            | Observability documentation                                       |
| observability/img        | Observability images                                              | 
| accelerators             | Accelerators  documentation                                       |
| accelerators/img         | Accelerators images                                               | 
| persona	           | Persona documentation                                             |
| persona/img              | Persona images	                                               | 
| solutionarchitecture     | Solution Architecture documentation                               |
| solutionarchitecture/img | Solution Architecture images                                      | 
| ccoetom                  | Cloud Center of Excellence & Target operating model documentation |
| ccoetom/img              | Cloud Center of Excellence & Target operating model images        |
| mfcpm                    | Mosiac Frame Client Program Management documentation              |
| mfcpm/img                | Mosiac Frame Client Program Management images                     |


### Adding Text

Adding text is simple and straight forward. Use the header "#" to create main heading, "##" to create the sub heading and so on.

Playbook is following a standard to start with "#" for main page for your topic, followed by "##" for main sections of the page & "###" for sub sections.


### Adding Table of Contents with in a page

Playbook allows to auto create table of contents based on the attributes assigned to sections. Below section explains creating
table of contents **within a page**


````markdown

# ROKS
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## ROKS Overview

ROKS is referred as Redhat Openshift Kubernetes Service also sometimes referred as Redhat Openshift on IBM Cloud

---

## ROKS Service Flows

---

In the above example, main page called "ROKS" will not be included in Table of contents, 
similarly sub heading of "Table of Contents" also will be excluded from the table of contents,
this is achived by using the no_toc variable.

After adding the built in "TOC" function, any heading below with "##" becomes a table of content.
Infact if you add sub heading using "###" under any heading, that also will be added to TOC automatically.


````
To see the results of above TOC example, click on button below

[TOC Example](https://pages.github.ibm.com/ISOM/Playbook/hmcp/roks/){: .btn .btn-blue }

### Adding Table of Contents for Child Pages

Table of content for child pages is populated automatically on main page. You need to define the **Front Matter** appropriately on the page.
See the example below

````markdown

Following Front Matter must be added to **All Pages** at the top of each page

For Parent Pages

---
layout: page
title: Parent_Page_Title
has_children: true   ---> This attribute is for parent page, comment out this line for the child page
parent: Page_Parent  ---> Add the "title" of your Parent page here, if this page is under ISOM Playbook, that becomes your parent
nav_order: 2         ---> Navigation order of your page
---

For Child Pages

---
layout: page
title: Child_Page_Title
#has_children: true   --> Comment this line of it has no further childrens
parent: Parent_Page_Title  --> This will place the child under parent mentioned above
grand_parent: ISOM Playbook --> This will ensure that pages are under tree of ISOM Playbook if your parent page was under ISOM Playbook
nav_order: 2 --> This is navigation order for your child page (if have multiple childs)
---

````


### Adding Images

Images should be kept in the subfolder/img directory, this ensures consistency across the portal

To reference a picture use following construct

````markdown

![image_title](<< site.baseurl >>/<subfolder>/img/<image>.<ext>)

<replace the "<<" & ">>" with opening & closing curly braces before and after site.baseurl, site.baseurl is a configured variable for the portal which points to root of website

````

### Using Command Line Terminal


Following steps can be used to edit the pages using CLI (mac or windows)

Before continuing the steps below, make sure you have added your SSH keys to the Github account. If you have not done so, follow the steps in below link

[Connecting to GitHub with SSH](https://docs.github.com/en/enterprise/2.20/user/github/authenticating-to-github/connecting-to-github-with-ssh)


Once you have added your ssh keys, start with the steps below

<br />

#### **Clone the Repository**

````markdown

Users/home/abc$  git clone git@github.ibm.com:ISOM/Playbook.git

````

Above command will clone the Playbook to your local machine in "Playbook" folder under your current working directory


####  **Make the modifications in local copy**


Navigate to the respective folder and file where you want to make changes. Use any editor to make the changes. Once done, save the file locally



#### **Commit your changes**

````markdown

Users/home/abc$ git commit -m "Updating XYZ file"

````

Above command will commit your changes, make sure you add the message using "-m" option defining your changes


####  **Push your changes**

````markdown

Users/home/abc$ git push origin gh-pages

````

Above command will push your changes to "gh-pages" branch, the changes you made should be reflected with in 10-15 seconds on the website

**Note** : It is always recommended to run a "git pull" before pushing your changes to ensure your local repository is up to date with the gh-pages branch.



