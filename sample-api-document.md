# Upload a sound file

Uploads a sound file for a user's profile.
<br><br>

## URL

```
POST https://api.fananthem.com/profile/sound
```

## Headers

| Header Name	| Description |	Required	| Values |
| :--- | :--- | :--- | :--- |
| **Bearer**	| The access token	| Required	| See Authorization section |
| **Content-Type**	| The format of the sound file to upload	| Optional	| audio/mpeg or audio/x-wav. Default is audio/mpeg. |
| **Accept**	| The format of the returned data	| Optional 	| application/xml or application/json. Default is application/json. |

<br>

## POST Body

The sound file.

**Note:** The sound file must be 3 minutes or shorter.
<br><br>

## Sample Request

```
POST https://api.fananthem.com/profile/sound

Bearer: {access token}
Content-Type: audio/x-wav
Accept: application/json

{sound file}
```

## Response

| Element	 | Description	| Type	| Notes |
| :--- | :--- | :--- | :--- |
| **id**	| The ID of the new sound file.	| integer	| |
| **length**	| The length of the sound file.	| float	| Length is in seconds. |

<br>

## Sample Response

```
{
   "id": 24643,
   "length": 48.5
}
```
<br><br>

# Retrieve a list of sound files

Retrieves a list of profile sound file URLs and their lengths for the specified user.
<br><br>

## URL

```
GET https://api.fananthem.com/user/{user id}/profile/sound
```
where `{user id}` is the ID of the user whose profile contains the sound files.
<br><br>

## Query Parameters

| Parameter	| Description	| Type	| Required	| Notes |
| :--- | :--- |  :--- | :--- | :--- |
| **sortOrder**	| The order to return the sound file information.	| string	| Optional	| Valid values: mostRecent, earliest, shortest, longest. Default is mostRecent. |

<br>

**Note:**
- mostRecent, sorts most recent to earliest
- earliest, sorts earliest to most recent
- shortest, sorts shortest to longest
- longest, sorts longest to shortest
<br><br>
 
## Headers

| Header Name	| Description |	Required	| Values |
| :--- | :--- | :--- | :--- |
| **Bearer**	| The access token	| Required	| See Authorization section |
| **Accept**	| The response format	| Optional 	| application/xml or application/json. Default is application/json.

<br>

## Sample Request

```
GET https://api.fananthem.com/user/15487/profile/sound?sortOrder=shortest

Bearer: {access token}
Accept: application/json
```

## Response

| Element | Description	| Type	| Notes |
| :--- | :--- | :--- | :--- |
| **soundFiles**	|	List of sound file information.	| array |	
|	&emsp;&emsp;&emsp;id	| The ID of the sound file.	| integer	|
|	&emsp;&emsp;&emsp;url	| The URL of the sound file.	| string	|
|	&emsp;&emsp;&emsp;length	| The length of the sound file.	| float	| Length is in seconds. |

<br>

## Sample Response

```
{
    "soundFiles": [
        {
            "id": 5687,
            "url": "https://api.fananthem.com/profile/sound/5687.mp3",
            "length": 110.2
        },
        {
            "id": 9874,
            "url": "https://api.fananthem.com/profile/sound/9874.mp3",
            "length": 93.8
        }
    ]
}
```

## Status Codes and Errors

The following table lists the returned HTTP status codes.

| Code	| Description	| Notes |
| :--- | :--- | :--- |
| 200	| OK	| Sound file was successfully added. |
| 401	| Unauthorized	| Access token is invalid. |
| 413	| Request Entity Too Large	| Uploaded sound file is longer than 3 minutes. |

