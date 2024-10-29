---
title: "Linux File Permissions Made Easy: Decode r, w, x, and Numeric Modes"
seoTitle: "Linux File Permissions: r, w, x Explained"
seoDescription: "Learn to decode Linux file permissions easily with symbolic and numeric modes. Master setting permissions using practical examples"
datePublished: Tue Oct 29 2024 18:26:37 GMT+0000 (Coordinated Universal Time)
cuid: cm2us4ggj000208lbavfyc512
slug: linux-file-permissions-made-easy-decode-r-w-x-and-numeric-modes
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1730226222385/19bc1fa7-0edd-4fd5-98fb-8e7bfaaeca77.jpeg
tags: linux, devops, file-permission, 90daysofdevops

---

### Introduction

Linux is renowned for its robust security model, and at the heart of this model are file permissions. Understanding how file permissions work is crucial for both system administrators and everyday users. In this article, we'll explore how to set and manage permissions using both `symbolic` (r, w, x) and `numeric` (4, 2, 1) representations. We’ll also provide practical use cases to solidify your understanding.

### Understanding File Permissions

In Linux, every file and directory has associated permissions that determine who can read, write, or execute them. The permissions are divided into three categories:

1. **User (u)**: The file's owner.
    
2. **Group (g)**: The group associated with the file.
    
3. **Others (o)**: Everyone else.
    

Each category can have three types of permissions:

* **Read (r)**: Allows reading the file or listing the directory contents.
    
* **Write (w)**: Allows modifying the file or adding/removing files in a directory.
    
* **Execute (x)**: Allows executing a file or accessing a directory.
    

### Identifying Files and Directories

When you list files in a directory using the `ls -l` command, you’ll see output similar to this:

```bash
drwxr-xr-- 2 user group 4096 Oct 29 12:00 my_directory
-rw-r--r-- 1 user group  204 Oct 29 12:00 my_file.txt
```

Here's how to interpret this output:

* The first character indicates the type:
    
    * `d`: Directory
        
    * `-`: Regular file
        
    * `l`: Symbolic link (not covered in this article)
        
* The next nine characters represent permissions for user, group, and others:
    
    * The first three (`rwx`) are for the owner (user).
        
    * The next three (`r-x`) are for the group.
        
    * The last three (`r--`) are for others.
        

In the example above:

* `my_directory` is a directory with read, write, and execute permissions for the owner, read and execute permissions for the group, and read permissions for others.
    
* `my_file.txt` is a regular file with read and write permissions for the owner and read permissions for the group and others.
    

### Numeric Representation of Permissions

Permissions can also be represented numerically, using the values 4, 2, and 1:

* **Read (r)** = 4
    
* **Write (w)** = 2
    
* **Execute (x)** = 1
    

To set permissions, you add the values corresponding to the desired permissions.

For example:

* To set read and write permissions (r + w), you would add 4 + 2 = **6**.
    
* To set read and execute permissions (r + x), you would add 4 + 1 = **5**.
    
* To set all permissions (r + w + x), you would add 4 + 2 + 1 = **7**.
    

### Setting Permissions: Examples

You can use the `chmod` command to set file permissions. The syntax is as follows:

```bash
chmod [permissions] [file/directory]
```

##### Example 1: Setting User Permissions

Imagine you have a file named `example.txt`, and you want the owner to have read and write permissions, while the group and others should only have read permissions.

Using numeric representation, you would set the permissions to `644` (owner: 6, group: 4, others: 4):

```bash
chmod 644 example.txt
```

### Using symbolic representation, you could achieve the same with:

```bash
chmod u=rw,g=r,o=r example.txt
```

##### Example 2: Setting Group Permissions

Suppose you have a script named [`script.sh`](http://script.sh) that you want to be executable by the owner and the group, but not by others. You would set the permissions to `770` (owner: 7, group: 7, others: 0):

```bash
chmod 770 script.sh
```

### Using symbolic representation, it would be:

```bash
chmod u=rwx,g=rwx,o= script.sh
```

> Please refer this document in case of more details [Linux file permissions explained](https://www.redhat.com/en/blog/linux-file-permissions-explained)

### **Conclusion**

Understanding Linux file permissions is essential for maintaining system security and ensuring that users have the appropriate access. By mastering both the numeric (4, 2, 1) and symbolic (r, w, x) representations, you can effectively manage file access in your Linux environment.

---

Thank you for reading! 🚀 If you found this guide helpful or have any suggestions, tips, or questions about Linux Permissions, please feel free to leave a comment below. I’d love to hear from you and learn together!

Don't forget to follow my blog for more awesome insights on development topics, and connect with me on [**LinkedIn**](https://www.linkedin.com/in/ahireshubham/) and [GitHub](https://github.com/Shubham-Ahire) to stay updated on all things tech and coding! 🎉