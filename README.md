# dspace-creative-commons-languages
Explanation on how to have multiple languages for the Creative Commons form.

## creative-commons.jsp
You must import the Java util Locale.  
`<%@ page import="java.util.Locale"%>`

In the script section near the top of the page, get the session locale with the UIUtil import.  
`Locale sessionLocale = UIUtil.getSessionLocale(request);`

At the bottom of the file, within the script tag running jQuery, the URL is changed to add in the locale.  
`url: '<%=request.getContextPath()%>/json/creativecommons?license=' + make_id + '&locale=<%= sessionLocale.toString() %>'`

## CreativeCommonsJSONRequest.java
Get the value that was passed in from the changed URL earlier from the locale=... value. You can put this following line right below where it gets the license parameter from the request.  
`String locale = req.getParameter("locale");`

Change the assignment of the ccLocale to your liking.  
`ccLocale = (StringUtils.isNotBlank(locale)) ? locale : ((StringUtils.isNotBlank(ccLocale)) ? ccLocale : "en");`
