# Monitoring and APIs

## Monitoring activations

IBM Cloud Functions (ICF) Web UI comes with a [comprehensive visualization dashboard](https://cloud.ibm.com/functions/dashboard) for monitoring invocations of actions and triggers within a region and namespace.

Developers can see activation results, invocation times, and logging output through the dashboard. An activation summary and timeline are displayed and can be filtered by action name.  Trigger invocations can also be excluded from the view. In the screenshot below, all activations for actions residing in the namespace `test-iam-namespace` are shown:

![Monitoring dashboard](images/101-ex5-monitoring.png)

Clicking on an activation ID in the "Activity Log" will show you the complete activation record in either raw or JSON format along with the HTTP request and response headers.

When things are going wrong with your actions, this dashboard will provide a nice starting point to debug the issue.

{% hint style="info" %}
If you wish to retain and create views on activations across your account, you can setup and connect ICF to the IBM Cloud logging service by clicking on the "Logs" item in the left menu.
{% endhint %}

## Managing APIs

HTTP endpoints for web actions can be created and managed through the ICF Web UI. Using this interface is often a lot more intuitive than using the CLI tool for managing more complex APIs.

1. Select "APIs" from the left-hand menu panel on the homepage.

![API homepage](images/101-ex5-api-list.png)

### Details overview

The API details page shows properties for the chosen API, including an API monitoring page showing invocations.

![API homepage](images/101-ex5-api-details.png)

Using the menu on the left-hand side, different properties for the API can be accessed and modified.

* **Summary** - API overview page and monitoring dashboard for API invocations.
* **Definition** - API configuration properties, allows updating properties live.
* **Sharing and Keys** - Configure the exposing API with your internal users.
* **API Explorer** - API documentation for your endpoints.

### Create API

Now that we have viewed the API we created from the CLI, let's create a new API using the web interface.

1. Return to the API listing page using the breadcrumb.

![Use APIs breadcrumb](images/101-ex5-api-breadcrumb.png)

2. Click on "Create API” button.

![Create new API](images/101-ex5-api-list-create.png)

3. Fill out the "API name" field as "myapi".

![Add API name](images/101-ex5-api-create-basic.png)

Notice that the "Base path for API" is automatically filled out using the name you entered by adding a leading forward slash.

4. Click on the "Create Operation" button.

![Crete operation](images/101-ex5-api-create-operation.png)

This will display a modal dialog.

5. Fill out the "Path" field as "/hello2" and select the `hello2` action we created earlier from the dropdown list and click "Create".

<!--
#######################################################
TODO: Figure out how to add width="40%" to this image.
#######################################################
-->
![Fill in operation information](images/101-ex5-api-create-operation-modal.png)

6. Scroll down to bottom and click "Create".

After creating the operation for your API. you are returned to the actual API create page.  You must scroll down to the bottom and click "Create" to actually create the API:

![Create API with operation](images/101-ex5-api-create-final.png)

{% hint style="tip" %}
As you may have noticed, you scrolled past *Security and Rate Limiting* and *CORS* options which are not covered in this course, but are valuable settings for real-world APIs that you can come back and try later.
{% endhint %}

{% hint style="info" %}
Although we just created an API with an operation manually, you can also use the OpenAPI specification and manage your APIs via Swagger documents.  In fact, using ICF, you can download the resulting Swagger for any API you create from the CLI or web UI.
{% endhint %}

### Explore API and Operation

Let's see what the completed API definition looks like in the web UI.

1. Select "Explore API" from the left menu.

![Explore our new API](images/101-ex5-api-greeting-explore.png)

The API's overview is shown along with its operations and public endpoint.

2. Select the `/hello2` *GET* operation

![Explore our the GET operation](images/101-ex5-api-greeting-explore-operation.png)

The "GET" operation's HTTP endpoint is displayed along with any declared  parameters and example `curl` command to invoke it from a command line.

{% hint style="info" %}
You can even copy the URL generated for your GET operation and try it from a browser window.
{% endhint %}

### Invoke API

Final;y, let's invoke the `greeting` API's *GET* operation.

1. Click the "Try it" tab.

![Try out API operations](images/101-ex5-api-greeting-explore-operation-tryit.png)

2. Click the "Send" button and view the results.

![HTTP request and response](images/images/101-ex5-api-greeting-explore-operation-tryit-result.png)

You should see the full HTTP request and response JSON objects with the expected "Hello World" message.

{% hint style="success" %}
Huge congratulations on exploring the ICF web UI! As you can see, you can do everything within the web UI that can be done from the IBM Cloud CLI with the Cloud Functions plugin and more.
{% endhint %}
