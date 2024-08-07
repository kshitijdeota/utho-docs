---
slug: Using hashes in redis
description: "Redis Hashes are maps of field and value pairs. In this guide, you learn how to use Redis hashes, maps of fields, and values frequently used for storing objects".
keywords: ['redis hashes example', 'accessing redis hashes', 'get redis hashes all key']
tags: ['redis server', 'redis']
published: 2024-07-11
modified_by:
  name: Utho
title: "Use Hashes in Redis Databases"
title_meta: "How to Use Hashes in Redis Databases"
authors: ["Pawan Kumar"]
tags: ["saas"]
---

Redis, the open-source NoSQL database, is widely adopted for caching, messaging, and various storage applications that demand high speed and low latency. Redis incorporates the hash data type, allowing storage of field-value pairs ranging from simple to highly complex data structures. This tutorial explains Redis hashes comprehensively, demonstrating how to create, access, and modify hashes with practical examples. By following this tutorial, you'll gain the necessary knowledge and tools to effectively utilize hashes in your Redis databases.

## Before You Begin

Review our Getting Started with Utho guide and follow the instructions to set up your Utho's hostname and timezone.

Throughout this guide, sudo is used wherever applicable. Follow the steps outlined in our How to Secure Your Server guide to set up a standard user account, strengthen SSH access, and eliminate unnecessary network services.

Ensure your system is up to date by performing a system update.

    - On **Debian** and **Ubuntu**, use the following command:

            sudo apt update && sudo apt upgrade

    - On **AlmaLinux**, **CentOS** (8 or later), or **Fedora**, use the following command:

            sudo dnf upgrade

Refer to our How to Install and Configure Redis guide for detailed instructions on installing a Redis server and command-line interface (CLI). Use the drop-down menu at the top of the page to select your Linux distribution and follow the relevant steps provided.

{{< note >}}
This guide is tailored for non-root users. Commands that require elevated privileges are prefixed with sudo. If you’re unfamiliar with the sudo command, refer to the Linux Users and Groups guide for more information.
{{< /note >}}

## What Are Hashes in Redis?

Redis Hashes are collections of field-value pairs, akin to hash structures found in programming languages such as Python and Ruby.

With hashes, you can have a single Redis entry (called a "key") with numerous field-value pairs. This essentially allows you to associate properties with a given item in Redis.

### Common Uses for Hashes

Hashes are especially useful for storing objects and similar values consisting of numerous properties. In fact, because of Redis's effectiveness for caching web applications, hashes are often used for storing data from JSON objects.

So, as an example, you might see hashes used for caching a user's web session. That can include everything from username to the user's current location in a document.

## How to Use Hashes in Redis

The following sections introduce you to using hashes in your Redis databases, highlighting some of the most useful commands. They include everything from creating hashes to accessing their values to modifying hash entries.

### Create and Modify Hash Entries

You can use the `HMSET` command to set field-value pairs on a hash. You can use this command to create a hash that does not yet exist.

    HMSET example_user_hash username example_user password example_password other_data example_other_data

In the command above, `example_user_hash` is the name of the hash. Following that is a series of paired field names and values: `username example_user`, `password example_password`, and `other_data example_other_data`.

The `HMSET` command can also be used to modify hash entries. Calling the command for one or more existing fields changes their values to the newly-provided ones.

#### Increment Hash Values

For fields with integer values, you can use the `HINCRBY` command to increase the value by a given amount, which can be a negative number. Below is a full example:

    HMSET example_hash first_field 10
    HINCRBY example_hash first_field 1

{{< output >}}
(integer) 11
{{< /output >}}

The same can be done for float values by using the `HINCRBYFLOAT` command:

    HMSET example_hash second_field 5.5
    HINCRBYFLOAT example_hash second_field -0.9

{{< output >}}
"4.6"
{{< /output >}}

### Fetch Hash Values

Use the `HMGET` command to fetch the values of fields in a hash. For instance, the following command gets the `username` and `other_data` fields' values from the `example_user_hash` that was created using the `HMSET` command in the section above.

    HMGET example_user_hash username other_data

{{< output >}}
1) "example_user"
2) "example_other_data"
{{< /output >}}

You can even use the `HRANDFIELD` to get one or more random field names from a hash. The command comes with a `WITHVALUES` option to view the returned fields with their values, or, alternatively, you can get the values using `HMGET`.

    HRANDFIELD example_user_hash 2 WITHVALUES

{{< output >}}
1) "other_data"
2) "example_other_data"
3) "password"
4) "example_password"
{{< /output >}}

#### Get All Fields and Values

Redis has several commands for listing all items in a hash, depending on what information you want about each item.

- Use the `HKEYS` command to get all of the fields in a Redis hash.

        HKEYS example_user_hash

    {{< output >}}
1) "username"
2) "password"
3) "other_data"
    {{< /output >}}

- Use the `HVALS` command to get all of the values for all of the fields in a hash.

        HVALS example_user_hash

    {{< output >}}
1) "example_user"
2) "example_password"
3) "example_other_data"
    {{< /output >}}

- Use the `HGETALL` command to list all of the field-value pairs. Field names are given with values on the following line (so field names are on odd numbers and values on even):

        HGETALL example_user_hash

    {{< output >}}
1) "username"
2) "example_user"
3) "password"
4) "example_password"
5) "other_data"
6) "example_other_data"
    {{< /output >}}

#### Check for Fields

To verify whether a field exists in a hash, you can use the `HEXISTS` command. Provide the command with a hash and a field name. The command returns `1` for true (the field exists in the hash) or `0` for false (the field does not exist in the hash).

    HEXISTS example_user_hash username

{{< output >}}
(integer) 1
{{< /output >}}

    HEXISTS example_user_hash test_field_name

{{< output >}}
(integer) 0
{{< /output >}}

### Delete Hash Values

Delete one or more specific fields from a hash using the `HDEL` command. The command takes the hash name followed by the names of the fields to be deleted.

    HDEL example_user_hash other_data password
    HGETALL example_user_hash

{{< output >}}
1) "username"
2) "example_user"
{{< /output >}}

You can also delete an entire hash using the `DEL` command.

    DEL example_user_hash

## Conclusion

By following this tutorial, you'll be equipped to effectively utilize hashes in your Redis databases. This capability can greatly enhance various storage tasks, particularly for object storage in web application caching. Explore additional Redis guides and tutorials for further insights, including topics such as Using Sorted Sets in Redis Databases and Using Lists and Sets in Redis Databases.
