---
title: Server-side data saving
teaching: 5
exercises: 20
questions: []
objectives:
  - Handle participant data sent to the server, and save it to the OSF.
keypoints:
  - Never trust data sent from the participant's computer.
  - Don't put your PAT on GitHub.
day: 1
order: 600000
missingDependencies: []
dependencies: []
originalRepository: mjaquiery/ukrn-test-workshop
summary: We'll create a `save_data.php` file to take the data and send it to the OSF, and a separate `secrets.php` file to hold our PAT.

---

Create a new file in the jsPsych quickstart project called `save_data.php`.

Paste the code below into the file:
> ## save_data.php
> ```php
> <?php
> /*
 > * secrets.php should contain the definition of the variable $OSF_PAT
 > * It should look like:
 > * <?php
 > * $OSF_PAT="osf_personal_access_token_with_osf.nodes.data_write_scope";
 > */
> include('secrets.php');
>
> // Your OSF data component id (https://osf.io/osf_repository_id/)
> $WHERE_TO_SAVE="26j4q";
>
> $content = $_POST['public_data']; // Data sent from the participant's machine
> $participant_id = $_POST['participant_id']; // Participant id sent from participant's machine
>
> // Because the above came from the participant's machine, we sanitize the input
> if(!preg_match("/^[0-9a-zA-Z]+$/", $participant_id)) {
>     http_response_code(400);
>     die("{error: 'Invalid participant Id'}");
> }
>
> // This may need changing if you don't use Frankfurt (DE) for your data storage
> $url = "https://files.de-1.test.osf.io/v1/resources/$WHERE_TO_SAVE/providers/osfstorage/?kind=file&name=$participant_id.csv";
>
> /*
>  * The cURL request below is adapted from https://stackoverflow.com/a/5676572
>  * We create a request to the $url above, with the following key properties:
>  * - PUT method (because we're creating a file)
>  * - Authorization header with the token
>  * - Body content of the file we want to create
>  */
>
> // open connection
> $ch = curl_init();
>
> // set the url, number of POST vars, POST data
> curl_setopt($ch,CURLOPT_URL, $url);
> curl_setopt($ch,CURLOPT_POST, true);
> curl_setopt($ch,CURLOPT_POSTFIELDS, $content);
> curl_setopt($ch, CURLOPT_CUSTOMREQUEST, "PUT");
>
> // set the request headers, used to authenticate using the PAT
> curl_setopt($ch, CURLOPT_HTTPHEADER, array(
>     "Authorization: Bearer $OSF_PAT"
> ));
>
> // have curl_exec return the contents of the cURL; rather than echoing it
> curl_setopt($ch,CURLOPT_RETURNTRANSFER, true);
>
> // execute post
> $result = curl_exec($ch);
>
> // Inform the participant that we saved the data successfully
> echo $result;
> ```
{: .solution}

Notice at the top of the file we `include('secrets.php')`.
`secrets.php` doesn't exist at the moment, so let's create that.

Its contents are explained in the comment in `save_data.php`: we need to declare a variable `$OSF_PAT` that holds the personal access token we created earlier.
Once you've done that, make sure `secrets.php` is listed in your `.gitignore` file (if you're using git) so that it doesn't get made public when you commit your changes.

We also need to edit `$WHERE_TO_SAVE` to point to the OSF component identifier we made a note of earlier.

With those changes made, we should be ready to go!
Do your experiment one more time, and you should see the success message that we wrote in `index.html`.
When you navigate to your OSF test component, you should see it has created a .csv file with your experimental data.

From now on, when participants complete your experiment, their data will be saved directly to the OSF.
When you access the data, you'll be accessing it in the same way that others do.
All that remains is to write a [data dictionary](https://help.osf.io/hc/en-us/articles/360019739054-How-to-Make-a-Data-Dictionary) so that others can understand the variables (don't worry too much if you don't understand all of the variables, just note down the ones you _do_ understand).

For this example, you can use the minimal data dictionary here:

| Variable | Name | Type | Description |
|----------|------|------|-------------|
| participant_id | Participant Id | string | A 15-character alphanumeric identifier for the participant |
| trial_type | Trial type | string | jsPsych plugin type |
| trial_index | Trial index | integer | jsPsych trial index |
| time_elapsed | Time since experiment start | integer | Milliseconds elapsed since the start of the experiment script |
| rt | Response time | double | Response time reported by the trial function in milliseconds |
| stimulus | Trial stimulus | string | Stimulus parameter for the trial function |
| response | Trial response | string | Response recorded by the trial function |
| task | Trial task | string | Friendly name for the trial_type |
| correct_response | Expected response | string | Response required for a correct response |
| correct | Correct response supplied? | boolean | Whether the response matched the correct_response |

You can copy this table and paste it into a spreadsheet program such as Microsoft Excel or Google Sheets, and then save in .CSV format as something like `data_dictionary.csv`.
Upload the saved file to your data component so that people accessing that component can use the dictionary.

Now you're done!
You now have
* participant data save automatically to the OSF
* data automatically made public and indexable by search engines
* a license that tells people what they can do with your data
* a data dictionary that tells people (including you in 6 months) what your variables mean and where they came from

> ## While we're here...
> You don't actually need to make the data public to upload them to the OSF.
> We could have kept the component private, and perhaps made it public later.
> If the component is private it doesn't need a license, but you should still include a metadata file, and you'll still need a PAT to upload data.
{: .solution}
