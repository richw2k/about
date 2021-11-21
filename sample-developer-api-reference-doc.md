# Fan Anthem API Reference Document

Fan Anthem is a new app that lets football fans upload original songs to their profiles and share with connected friends and member groups, with some hoping they'll score a firm favourite that's chanted from the terraces.

The following is a basic example of a reference document written by a Fan Anthem developer. It includes info on how sound files are uploaded to a user's own profile and how to get information on sound files for a user. 

See the [final API documentation](https://github.com/richw2k/tech-writer/blob/main/sample-api-document.md) I created based on this information.

**Note:** Useful information has been purposely omitted to simulate a real-world scenario. A tech writer will use their experience as well as testing the API and asking developers for more info to complete the task.<br><br>

## Uploading a Sound File to the current User’s Profile 

- The server address is https://api.fananthem.com 
- The resource is /profile/sound 
- There are three headers: 
    - Bearer has the access token. Required. 
    - Content-Type has the sound file format, which can be either audio/mpeg for mp3 files, audio/mp4 for m4a files or audio/x-wav for wav files. Default is audio/mpeg. 
    - Accept has the response format, which can be application/xml or application/json.
- The POST body is the sound file 
- The title of the audio file will be set to that of the name of the uploaded file
- The sound file can be max 3 minutes long.
- The response has two elements: 
    - id: An integer, which is the ID of the new sound file 
    - length: A float, which is the length of the sound file, in seconds<br><br> 
 
 
## Retrieving Sound File Information for a User 

- The server address is https://api.fananthem.com 
- The resource is /user/{user id}/profile/sound.  
- There are two headers: 
    - Bearer has the access token. Required. 
    - Accept has the response format, which can be application/xml or application/json. 
- There is one query parameter called sortOrder. This determines the order that the sound files are returned. It has four possible values: 
    - mostRecent, sorts most recent to earliest 
    - earliest, sorts earliest to most recent 
    - shortest, sorts shortest to longest  
    - longest, sorts longest to shortest 
- The sortOrder parameter is optional. The default is mostRecent. 
- Sample response: 
```
{ 
  "soundFiles": [     {       
       "id": 5687, 
       "url": "https://api.sounddate.com/profile/sound/5687.mp3", 
       "length": 110.2 
    }, 
    {       
       "id": 9874, 
       "url": "https://api.sounddate.com/profile/sound/9874.mp3", 
       "length": 93.8 
    }   ] 
} 
```

## Status Codes and Errors 
 
- 200, success for both POST and GET 
- 401, access token is no good 
- 413, sound file that was POSTed was too long 
