---
title: Setting up an OSF Data Component
teaching: 2
exercises: 10
questions: []
objectives:
  - Have an OSF project component ready to house the data
keypoints:
  - We use the _test_ subdomain of the OSF because we're testing things
day: 1
order: 300000
missingDependencies: []
dependencies: []
originalRepository: mjaquiery/ukrn-test-workshop
summary: We'll create a project and a data component on the OSF where we'll upload our data.

---

> #### Note:
> We'll be using the [test subdomain](https://test.osf.io/) of the OSF because we're testing things.

We'll be creating a new project on the Open Science Framework and adding a component which will house the data we upload.

1. Open [test.osf.io](https://test.osf.io/) in your browser and log in
2. Click 'Create new project'
![OSF new project screenshot](../fig/osf-new-project.jpg)
Then fill in the form:
![OSF new project form screenshot](../fig/osf-new-project-form.jpg)
Then click 'Go to project'
![OSF navigate to new project screenshot](../fig/osf-go-to-new-project.jpg)
3. Create a new project component.
This component will house the data.
![OSF new component screenshot](../fig/osf-new-component.jpg)
Fill in the form, making sure you select the **location** as `Germany - Frankfurt`.
![OSF new component form screenshot](../fig/osf-new-component-form.jpg)
4. Navigate to the new component and give it an open license.
CC-BY 4.0 is a good license to use - people are free to reuse the contents provided that they acknowledge that they got it from you.
![OSF add license screenshot](../fig/osf-project-license.jpg)
Now we have provided a license, let's make this component public.
Click 'Make Public'
![OSF make public screenshot](../fig/osf-make-public.jpg)
5. Make a note of the component's id - we'll need that later.
You can find the id in the browser's address bar; it's the part that's highlighted in the screenshot below.
![OSF component identifier screenshot](../fig/osf-component-id.jpg)

You're now all set up with an OSF project which has a special component ready to hold all the raw data.


