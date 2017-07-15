# Concepts and Terms

**Vulnerability:**
A vulnerability is a weakness in your application that an attacker could potentially exploit. This can be weakness in the code itself or perhaps even an application design flaw.

**Exploit:**
An exploit is a malicious application or a set of commands used to take advantage of vulnerabilities in your application. The purpose of an exploit is to produce some unexpected or unintended behavior in your application, such as exposing sensitive information or gaining unauthorized access to certain components.

**Countermeasure:**
A countermeasure is a step taken to address or reduce the potential for damage caused by a vulnerability in your application code.
Threat / Threat Agent:
A threat is an event that could exploit a vulnerability in your application code and cause some undesirable behavior. Malicious hackers, or attackers, are often called threat agents because they exploit vulnerabilities in your application code to meet their objectives.

**Attack:**
An attack is an action that leverages one or more vulnerabilities to realize a threat. For example, a malicious hacker may exploit a vulnerability in your authentication system to gain unauthorized access to an area of your application.

**Asset:**
An asset is a resource of value. For example, an asset to your organization may be a database of the health or financial information of your customers.

**Risk:**
Finally, risk is the potential for loss or damage to an asset. Whenever a developer follows insecure coding practices, they increase the risk that an attacker may be able to exploit the flawed code.
 
 

 
# Managing Application Security Risks:
No application can be completely secure or resilient to all attacks!

Four Main Approaches to managing risk.

1 Acceptance

2 Avoidance

3 Transference

4 Mitigation

Accepting risk means that you take no proactive measures to address your risk and that you are willing to accept the full consequences of a threat to an asset. Usually, you should use this approach only as a last resort. When accepting risk, you should always have a contingency plan, which is a set of actions you plan to take if the risk is realized.

Avoiding risk is the opposite of accepting risk. To avoid risk, you remove the exposure of an asset to the threat, or you remove the asset entirely.

This leads us to the next risk management technique called transference, which means you transfer the burden of the risk onto a third party. For example, instead of handling card information yourself, you may elect to pay a third-party with expertise in the payment card industry to handle it for you, thus transferring the risk to them. Insurance is a classic example of transferring risk.

The final risk management approach is to mitigate risk, which means that you take proactive steps to reduce an asset’s exposure to a risk. For example, you can reduce the risk of an attacker guessing user account passwords by requiring all users to use strong passwords. Or, to reduce the chances of an attacker intercepting sensitive data transmitted between your online application and users, you could protect the data in transit by using Transport Layer Security (TLS). Mitigation is the most common and recommended way to address application security risks. It should be your primary approach to managing application security risk.
 

 
# Anatomy of a Basic Application Attack
Any method that allows data to be input to an application is considered an interface. Common types of user interfaces include web forms, command line parameters, and APIs.

An attacker interacts with your application in order to perform nefarious actions. To do this, attackers identify a vulnerability they can exploit to submit malicious data to the application in order to execute an unintended command or action, for example, an attacker could supply a malicious data that would cause your application to execute a command, expose sensitive information, or even cause your application to crash making it unavailable to users.

As a developer, it is vital to counter measures to ensure your application accepts only valid data and blocks malicious data. This process is referred to as input validation. Input validation helps verify that input is in a correct and safe format to be used by your application. While not a silver bullet, input validation can be used to help mitigate many common application vulnerabilities.

What are the primary techniques for validating data? How do you determine if data is valid or not? This leads to the next topic in our discussion, input validation techniques.

## Whitelist Validation with RegEx
Regular expressions provide a structured method for concise pattern matching that you can use to implement whitelist validation. Several regular expression libraries are available, and many programming languages have built-in regular expression support. For example, the .NET Framework and Java programming languages natively support regular expressions.

To use regular expressions, you first define regular expressions that describe expected input data types, ranges, formats, and lengths where appropriate. You then compare the input received by your application against the corresponding regular expression. If the input does not match the regular expression, it should be considered bad and rejected. If the input matches the regular expression, then it is considered safe and can be used.

## Blacklist Validation
Rejects only known bad input, and allows everything else. Its inherent weakness is that the set of all bad inputs is potentially infinite and cannot be completely detected, whereas the whitelist approach models a finite set and is easier to implement and less prone to error. Therefore, always use whitelist validation, and use blacklisting only as a supplementary measure.
 

 
### Common Application Attacks
* Buffer overflows
* SQL Injection attacks
* Race conditions

Buffer Overflow:
Buffer overflows occur in applications where more data is written into a buffer than that buffer has been allocated to handle. The result is that memory adjacent to the buffer gets overwritten, which typically causes the application to behave incorrectly or crash.
Buffer overflows can be exploited whenever an application attempts to write untrusted data into a fixed-length buffer without first validating the input or accurately calculating the buffer size.
Stack-Based Overflows:
Stack-based buffer overflows are caused by the fact that data is written into a local buffer without proper bounds checking. When a function is called, a stack frame is pushed onto the program stack. The program stack consists of the function’s parameters, the return address, the frame pointer, and the function’s local variables. When a local buffer is overflowed, following memory locations on the stack including the return address of the function end up being overwritten by user data. This poses a security issue because the return address determines the location of the next instruction to be executed after the function returns. This means that if an attacker can control the value of a function’s return address he can potentially control execution of the vulnerable program.
SQL Injection:
SQL injection vulnerabilities are yet another example of attacks that are possible due to the failure of applications to validate un-trusted data. SQL Injections are one of the most common attacks today. One reason is the ubiquity of SQL Data Stores, which increases the SQL injection attack surface. Another reason may be that many applications are moving toward the Web, which makes them more accessible to attack than traditional applications that reside within restricted internal networks. Finally, nearly all modern day database management systems support SQL. This means that malicious users need only learn the SQL language once and then they are able to apply those attack skills to virtually any database management system, regardless of the vendor platform (Microsoft, Oracle, IBM, MySQL, and so on).
 
 
Preventing SQLi: Use Parameterized APIs
While input validation can be used to mitigate the risks from many attacks, there may be times where input validation alone may not be sufficient. In the case of SQL injection, it may be hard to validate input where the structure of the input is unknown or undefined, such as in a product review.
As a good security practice, type-safe SQL command parameters should be used in all situations where any variables are included in a SQL statement. Type-safe SQL command parameters indicate to the database engine that the data defined in certain parameters are values only and should never be executed. Marking input data as non-executable neutralizes any SQL commands that a malicious user may try to inject and is extremely effective for mitigating risk from SQL injection attacks.
To properly use parameterized APIs for database access, you should:
·         Identify available database access APIs. Review the database API used by your application and determine if parameterized statements are supported.
·         Choose whether to use parameterized statements or parameterized stored procedures. Parameterized statements are typically easier to use, but if those are unavailable then use parameterized stored procedures instead.
·         Identify all the SQL queries performed by your application.
·         Once you have located all SQL queries, identity the parameters in each query for their format and type.
·         Use your chosen parameterized API to execute each SQL query made by your application.

Secure Application Development Principles and Best Practices
Secure coding principles are coding practices which, when followed, can greatly increase the security of an application. There is no one principle that will render your application free from security vulnerabilities, together these key principles can help you greatly improve your overall security posture:
·         Use input validation
·         Use standard security libraries
·         Use language, compiler, and platform protection
·         Perform code analysis and code review
·         Leverage vendor technology security guidance
·         Leverage application security models, standards, and guidelines


Input Validation Best Practises
Recall that input validation verifies that input is in a correct and safe format before it is used by your application. It is a critical component of any application security strategy and when properly implemented, it is considered the most effective method for mitigating risk from nearly every known application vulnerability. As a general rule, any untrusted input should be validated. When in doubt, perform input validation anyways.
Code Analysis and Code Review
The next secure development principle is to use code analysis tools and code review.
Code analysis tools are software-based tools that inspect application source code in either compiled or non-compiled forms for known defects. These tools can be categorized into static analysis and binary analysis. The details of these two tool categories will be discussed momentarily.
Code review is the manual inspection of application source code typically by a security analyst.
Both code analysis and code review are an important component of any secure application development effort. They allow you to detect and correct vulnerabilities in legacy applications, as well as detect and correct vulnerabilities in current applications fairly early in the development lifecycle, where the cost of fixing vulnerabilities is low.
Code Analysis
All applications are first expressed as source code. These are the human readable instructions created by developers that implement software, such as Java code.
A compiler and linker takes that source code and turns it into machine code, often called an application binary.
The key difference between static analysis tools and binary analysis tools is the input into these tools. Static analysis tools analyze source code, while binary analysis tools analyze application binaries. Each have specific benefits and limitations which we will discuss next.
Static Analysis
Compared to manual code reviewers, static analysis software tools can scale fairly easily to analyze large amounts of code, and they are objective and unbiased. When compared to binary analysis, static analysis technology is generally more mature. Static analysis tools tend to find more vulnerabilities and provide more accuracy than binary analysis tools. Finally the issues identified by static analysis tools are easier to debug, since they work with human readable source code rather than compiled code.
Static analysis tools also have certain limitations. First, they read source code and are language specific, so organizations that use many programming languages may require many static analysis tools. In addition, they may produce false positives by flagging items that are not vulnerabilities, and produce false negatives by missing actual vulnerabilities. This often creates more work for development teams, and can eventually degrade confidence in these tools. Finally, static analysis tools can only find implementation flaws, that is, specific coding patterns that lead to vulnerabilities. They cannot necessarily detect flaws related to the business logic of the application.
Binary Analysis
Now let’s take a look at some pros and cons of binary analysis tools.
Like static analysis tools, binary analysis tools can scale to review large amounts of code, and are more objective and unbiased than human reviewers. And, binary analysis tools are more accurate than static analysis tools. This is because binary analysis tools operate on the actual code that gets executed, whereas static analysis tools operate on source code, which may get optimized and re-arranged by compilers.
However, binary analysis tools do have limitations. They are far less mature when compared to static analysis tools, so the breadth of vulnerabilities that they can detect is limited for now. Also, the bugs identified by binary analysis tools are difficult to debug, since developers have to be able to interpret compiled code. Finally, binary analysis tools suffer from the same limitations as static analysis tools: They are language-specific, so organizations may require many tools; they produce false positives and false negatives; and they are unable to detect issues other than implementation flaws.
Manual Code Review
Manual code review has benefits and limitations of its own.
To begin with the benefits: Manual code reviews have the distinct advantage over code analysis of generally producing fewer false negatives and false positives. And, human code reviewers can find not only the implementation flaws, but also flaws in design and in business logic.
While manual code review provides some great benefits, it does come with certain limitations. First, manual code review is very time consuming and does not scale very well. Another limitation is that reviewers can become fatigued from reviewing large amounts of code, which diminishes their ability to accurately identify vulnerabilities. In addition, different reviewers have different areas of expertise, so different vulnerabilities may get identified depending on who reviews the code.
