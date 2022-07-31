<div align='center'>
    <h1>JSP</h1> 
    <a class="header-badge" target="_blank" href="https://www.linkedin.com/in/saurabhmchavan/">
          <img src="https://img.shields.io/badge/style--5eba00.svg?label=LinkedIn&logo=linkedin&style=social">
    </a>   
    <a class="header-badge" target="_blank" href="https://twitter.com/100rabhcsmc">
          <img src="https://img.shields.io/badge/style--5eba00.svg?label=twitter&logo=twitter&style=social">
    </a>
    <a class="header-badge" target="_blank" href="https://instagram.com/100rabhch">
          <img src="https://img.shields.io/badge/style--5eba00.svg?label=instagram&logo=instagram&style=social">
    </a>
    <a class="header-badge" target="_blank" href="https://stackoverflow.com/users/12053852/saurabh-chavan?tab=profile">
          <img src="https://img.shields.io/badge/style--5eba00.svg?label=stackoverflow&logo=stackoverflow&style=social">
    </a>
 </div>

<div align='center'>
    <h1> JSP</h1> 
</div>

► JSP is Java Server Page, which is a dynamic web page and used to build dynamic websites. JavaServer Pages (JSP) is a technology for developing webpages that supports dynamic content.
► This helps developers insert java code in HTML pages by making use of special JSP tags, most of which start with <% and end with %> > JSP is dynamic file whereas Html file is static. > HTML cannot get data from database or dynamic data,
► JSP can be interactive and communicate with database and controllable by programmer.
► It is saved by extension of .jsp.
► Each Java server page is compiled into a servlet before it can be used. This is normally done when the first request to the JSP page is made.

| Servlet                                                           | JSP                                                                                |
| ----------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| Coding of Servlet is harden than jsp                              | Coding of jsp is easier than Servlet.                                              |
| Servlet is faster than JSP                                        | JSP is slower than Servlet because it first translate into java code then compile. |
| Writing code for servlet is harder than JSP as it is html in java | JSP is easy to code as it is java in html.                                         |
| In MVC architecture Servlet acts as controller.                   | In MVC architecture JSP acts as view..                                             |
| Servlet accept all protocol request.                              | JSP will accept only http protocol request.                                        |
| In Servlet we do not have implicit object.                        | In JSP, we have implicit object support.                                           |

##JSP Life Cycle
The following are the paths followed by a JSP
Compilation
Initialization
Execution
Cleanup

The four major phases of a JSP life cycle are very similar to the Servlet Life Cycle.

**JSP Compilation**
When a browser asks for a JSP, the JSP engine first checks to see whether it needs to compile the page. If the page has never been compiled, or if the JSP has been modified since it was last compiled, the JSP engine compiles the page.

The compilation process involves three steps -

1. Parsing the JSP.
2. Turning the JSP into a servlet.
3. Compiling the servlet.

**JSP Initialization**
When a container loads a JSP it invokes the jspInit() method before servicing any requests.

Typically, initialization is performed only once and as with the servlet init method, you generally initialize database connections, open files, and create lookup tables in the jspInit() method.

```
public void jspInit() {
  // Initialization code...
}
```

**JSP Execution**
This phase of the JSP life cycle represents all interactions with requests until the JSP is
destroyed.
► Whenever a browser requests a JSP and the page has been loaded and initialized, the JSP engine invokes thejspService() method in the JSP.
► The jspService() method of a JSP is invoked on request basis. → This is responsible for generating the response for that request and this method is also responsible for generating responses to all seven of the HTTP methods, i.e, GET, POST,
DELETE, etc. > This method takes HttpServletRequest & HttpServletResponse as parameters.

```

void _jspService(HttpServletRequest request, HttpServletResponse response)
{
// Service handling code...
}
```

**JSP Cleanup**
► The destruction phase of the JSP life cycle represents when a JSP is being removed from use by a container.
► This method is the JSP equivalent of the destroy method for servlets.
It performs any cleanup, such as releasing database connections or closing open files.

```
public void jspDestroy()
{
// Your cleanup code goes here
}
```

##Implicit objects used in JSP
| Servlet| JSP|
| ------------ | --------------------- |
|request|This is the HttpServletRequest object associated with the request. It is an instance of a javax.servlet.http.HttpServletRequest object. Each time a client requests a page the JSP engine creates a new object to represent that request. The request object provides methods to get the HTTP header information including form data, cookies, HTTP methods etc.
|response|This is the HttpServletResponse object associated with the response to the client. It is an instance of a javax.servlet.http.HttpServletResponse object. The response object also defines the interfaces that deal with creating new HTTP headers. Through this object the JSP programmer can add new cookies or date stamps, HTTP status codes, etc
|out|This is the PrintWriter object used to send output to the client. It is an instance of a javax.servlet.jsp.JspWriter object. It is used to send content in a response
|session|This is the HttpSession object associated with the request. It is an instance of javax.servlet.http.HttpSession and behaves exactly the same way that session objects behave under Java Servlets. The session object is used to track client session between client requests.
|application|This is the ServletContext object associated with the application context. It is an instance of a javax.servlet.ServletContext object. This object is a representation of the JSP page through its entire lifecycle. This object is created when the JSP page is initialized and will be removed when the JSP page is removed by the jsp Destroy() method

##A JSP contains 3 important types of elements:
**1) Directives**
These are messages to the JSP container that is the server program that executes JSPs.
a) page Directives
b) include Directives
c) taglib Directives

**2) Scripting elements**
These enable programmers to insert java code which will be a part of the resultant servlet.
a) Declaration
b) Expressions
c) Scriptlet
d) Comment

**3) Actions**
Actions encapsulates functionally in predefined tags that programmers can embedded in a JSP

**JSP Directives**
Directives are message to the JSP container that enable the programmer to specify page setting to include content from other resources & to specify custom tag libraries for use in a JSP.
**Syntax**
<%@ directive attribute = "value" >

| Directive | Description                                                                                                                                                                             |
| --------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| page      | Defines page settings for the JSP container to process                                                                                                                                  |
| include   | Causes the JSP container to perform a translation-time insertion of another resource's content. The file included can be either static ( HTML file) or dynamic (i.e., another tag file) |
| taglib    | Allows programmers to use new tags from tag libraries that encapsulate more complex functionality and simplify the coding of a JSP.                                                     |

**1) Page Directive**
The page directives specify global settings for the JSP in the JSP container. There can be many page directives, provided that there is only one occurrence of each attribute

```
*Syntax**
<%@ page
[ language="java" ]
[ extends="package.class" ]
[ import="{package.class package. *}, ..." ]
[ session="true false" ]
( buffer="none|8kb/sizekb" ]
[ auto Flush="true false" ]
[ is ThreadSafe="true false" ]
[ info="text" 1 ]
[ error Page="relativeURL"]
[ contentType="mimeType [ ; charset=character Set ]"
| "text/html; charset=ISO-8859-1" ]
[ isError Page="true/false" ] I pageEncoding="character Set | ISO-8859-1" 1 %>
```

**Example**
<%@ page import="java.util.\*" %>
<%@ page contentType="text/html" %>

**2) Include Directive**
►The include directive adds the required resource in a JSP page.
►Include directive tells the container to add the defined resource content in line to the JSP page during the translation time.
►This ensures reusability of the code such as code for navigation bar or standard heading which is displayed in every JSP Page.
►The include directive is used to include a file during the translation phase. This directive tells the container to merge the content of other external files with the current JSP during the translation phase.
►You may code the include directives anywhere in your JSP page.

**Syntax**
<%@include file ="relativeURL"%>

**Example:**
<%@include file="date.jsp"%>

**3) Taglib Directive**
► Taglib directive allows a JSP page to work with custom tags libraries.
►The JSP API allows you to define custom JSP tags and a tag libraries a set of user defined tags that implements custom behavior.
►The taglib directive declares that your JSP page uses a set of custom tags, identifies the location of the library, and provides means for identifying the custom tags in your JSP page.

**Syntax**
<%@taglib uri ="taglib URI" prefix="tag prefix"%>

Where URI is uniform resource locator, which is used to identify the location of custom tag and tag prefix is a string which can identify the custom tag in the location identified by uri.

**Example**
<%@ taglib uri="http://www.sample.com/mycustom lib" prefix="mytag" %>

##Scripting Elements
Scripting elements are used to insert the java code into JSP page. To manipulate the objects & perform some computation on an object or runtime value, scripting elements are used.

**1) Declarations**
A JSP element provides embedded JAVA declaration statements to be inserted into the
servlet class. → A declaration declares one or more variables or methods that you can use in Java code later
in JSP page

► You can declare any number of variables or methods within one declaration elements as long
as you end each declaration with a semicolon. Syntax <%! Java declaration statements %>

**Example**
<%! int count = 0; %>
<%! int a,b,c; %>
<%! Circle ob=new Circle(5); %>

**2) Expressions**
►A JSP element that provides the embedded JAVA expressions to be executed as part of the service method of the servlet class.
► An expression element contains a java expression that is evaluated, converted to a String, and
inserted where the expression appears in the JSP file.
► You cannot use semicolon to end an expression

**Syntax**
<%= expression %>

**Example**
Your name is <%=request.getParameter("name") %>
The value of PI = <%= Math.PI %>
Today's date is<%=new java.util.Date()%>

**3) Scriptlet**

►A JSP element that provides the embedded JAVA statements to be executed as part of the service method of the servlet class.
► A scriptlet contains a set of java statements which is executed.
► A scriptlet can have java variable and method declarations, expressions, use implicit objects
and contain any other statement valid in java.
► Scriplet are used to provide business logic in JAVA.

**Syntax**
<% statements %>

**Example**

```
<%
int a,b,c;
a = request.getParameter("t1");
b = request.getParameter("t1");
c=a+b;
out.println("Addition = " +c);
%>
```

**4) Comments**
► A JSP element that represents comments.
► JSP comments are used for documentation,
► In JSP Page JSP comment & HTML comment are available.
► The JSP comment is used to comment upon the purpose of the instruction in a JSP page.
► The comments are not displayed in the output to the client.

**Syntax**
JSP Comment :- <% -- comment --%>
HTML Comment :- <! -- comment -->

**Example**
JSP Comment :- <% -- This is JSP comment --%>

**Write a JSP program to check whether given number is Perfect or not.
(Use Includedirective).**

```
//Check.jsp
<%!
public boolean isPerfect(int n)
{
      int sum=0;
      for(int i=1;i<n; i++)
       {
          if(n%i==0)
             {
               sum=sum + i;
              }
        }
       return sum==n;
 }
%>

//Perfect.html

<html>
<form method=post action="Perfect.jsp">
Enter Number:<input type=text name="t1"><br><br>
<input type=submit value="SUBMIT">
<input type=reset value="RESET">
 </form>

//Perfect.jsp

<%@include file="Check.jsp"%>
<%
     int n = Integer.parseInt(request.getParameter("t1"));
     if(isPerfect(n))
         out.print(n+" is Perfect Number");
     else
        out.print(n+" is not an Perfect Number");
%>
```

**Write a JSP program to calculate sum of first and last digit of a given number.
Display sum in Red Color with font size 18.**

```
/Sum.html
<html>
<form method=post action=Sum.jsp>
Enter Number<input type=text name="t1"><br><br>
<input type=submit value="SUBMIT">
<input type=reset value="RESET">
</form>
</html>

//Sum.jsp
<%
       String number = request.getParameter("t1");
       int len=number.length();
       int a = number.charAt(0)-'0';
       int b = number.charAt(len-1)-'0';

        int sum = a+b;
%>
<font size=18 color='red'> Sum = <%=sum%>
</font>
```

**Write a JSP script to validate given E-Mail ID.**

```
//email.html
<html>
  <form method=post action="email.jsp">
  Email:<input type=text name="email"><br><br>
  <input type=submit value="SUBMIT">
  <input type=reset value="RESET">
  </form>
</html>

l/email.jsp
<%
String email = request.getParameter("email");
  int i = email.indexOf('@');
  int j = email.lastIndexOf('@');
  int k = email.indexOf('.');
      if(i!=-1 && j!=-1 && i==j && k!=-1 && k>i)
          out.print(email+" is valid email.");
      else
          out.print(emailt" is invalid email.");
%>
```

**Write a JSP program to create an online shopping mall. User must be allowed to
do purchase from two pages. Each page should have a page total. The third page should display a bill, which consists of a page total of whatever the purchase has been done and print the total. (Use Session)**

```
//Page1.html
<html>
   <form method=post action="Page1.jsp">
      <h2>Page 1</h2>
      <h2>Select Your Product</h2>
      <input type=checkbox name=CB value=10>
      Pencil : 10<br><br> <input type=checkbox name=CB value=20>Pen : 20<br><br>
      <input type=checkbox name=CB value=5>Eraser: 5<br><br>
      <input type=checkbox name=CB value=10> Scale 10<br><br>
      <input type=checkbox name=CB value=50>Note Book : 50<br><br>
      <input type=submit value="SUBMIT"> <input type=reset value="RESET">
    </form>
</html>

//Pagel.jsp
 <%
    String s[] = request.getParameterValues("CB");
    int total=0;
    for(int i=0;i<s.length;i++)
    {
        total=total+Integer.parseInt(s[i]);
    }
     session.setAttribute("totall", total);
     response.sendRedirect("Page2.html");


//Page2.html
<html>
   <form method=post action="Page2.jsp">
   <h2>Page 2</h2>
   <h2>Select Your Product</h2>
   <input type=checkbox name=CB value=500>Shirt : 500<br><br>
   <input type=checkbox name=CB value=400>T-Shirt : 400<br><br>
   <input type=checkbox name=CB value=1000>Jeans : 1000<br><br>
  <input type=checkbox name=CB value=750> Trouser : 750<br><br>
  <input type=checkbox name=CB value=1500>Saree : 1500<br><br>
  <input type=submit value="SUBMIT"> <input type=reset value="RESET">
</form>
</html>

//Page2.jsp
<%
String s[] = request.getParameterValues("CB");
int total=0;
for(int i=0;i<s.length;i++)
{
   total=total+Integer.parseInt(s[i]);
}
int total1= Integer.parseInt(session.getAttribute("totall").toString();
%>

<h2>Total Bill </h2> <table border=1>
<tr>
<td><b>Page 1:</b></td>
<td>Rs.<%=total1%>/-</td>
</tr>

<tr>
<td><b>Page 2:</b></td> <td>Rs.<%=total%>/></td>
</tr>

<tr>
<td>
   <b>Grand Total:</b>
</td>

<td>Rs.<%=totall+total%>/>
</td>
</tr>
</table>

```

**Write a JSP program to display the details of College (CollegeID, Coll_Name,
Address) in tabular form on browser.**

```
//College.html
<html>
    <form method=post action="College.jsp">
    Enter College ID<input type=text name="t1"><br><br> Enter College Name<input type=text name="12"><br><br> Enter College Address<input type=text name="t3"><br><br>
    <input type=submit value="SUBMIT">
</html>

//College.jsp
<center>
   <h2>College Information</h2> <table border=1>
   <tr>
       <th>Name</th>
       <th>Value</th> </tr>
  <tr>
    <td>College ID</td>
    <td><%=request.getParameter("t1")%></td>
  </tr>
   <td>College Name</td>
     <td><%=request.getParameter("t2")%></td>
   </tr>
   <tr>
    <td>College Address</td>
     <td><%=request.getParameter("t3")%></td>
   </tr>
</table
</center>
```

**Write a JSP program to accept Name and Age of Voter andcheck whether he is eligible for voting or not.**

```
// Age.html
<html>
   <form method=post action="Age.jsp">
    Enter Name<input type=text name="t1"><br><br>
    Enter Age<input type=text name="12"><br><br>
    <input type=submit value="SUBMIT">
    <input type=reset value="RESET">
    </form>
</html>

//Age.jsp
<%
     String name = request.getParameter("t1");
     int age = Integer.parseInt(request.getParamete("t2"));
     if(age>=18)
     {
        out.print(name+" you are eligible for voting");
    }else{
        out.print(name+"you are not eligible for voting");
    }
%>
```
