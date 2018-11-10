# Documentation

Service WebSocket accessible via l'adresse ws://perso.mog-creations.com:4442/  
Un code d'exemple en JavaScript est disponible à la fin de ce document.  

Tous les packets envoyés apr le service sont en format JSON.  

Le format des packets correspond à celui-ci:  
```json
{
  "type":"<type_du_packet>",
  ...
}
```

La variable `type_du_packet` représente le type du packet qui a été reçu ou envoyé.

Le serveur a besoin d'une preuve d'activité par le client. Le client doit envoyer un packet `PING` au serveur au moins toutes les 30 secondes. Le serveur considèrera que le client est déconnecté si aucun packet `PING` n'est reçu au bout de 30 secondes, et déconnectera ledit client.  
Le serveur répondra `PONG` à chaque `PING` envoyé par le client. Si le packet `PONG` n'est pas reçu au bout de 5 secondes après l'envoi d'un packet `PING`, le développeur peut considérer que la connexion au serveur a été perdue.

Format d'un packet `PING`:  
```json
{
  "type":"PING"
}
```

Format d'un packet `PONG`:
```
{
  "type":"PONG"
}
```

## Réception d'un nouveau Tweet

Lorsqu'un nouveau tweet est créé sur le Hashtag #zevent, #zevent2018 ou contenant le mot clé zevent, un packet `TWEET` sera envoyé à tous les clients connectés au service.  

Format du packet `TWEET`:

```json
{
	"type":"TWEET",
	"data": {
		"createdAt":1541817856000,
		"id":1061087112542478336,
		"text":"Je fais des tests rigolos pour le #zevent, si y'a des devs qui me suivent, dans quelques minutes je vous link une doc :)",
		"displayTextRangeStart":-1,
		"displayTextRangeEnd":-1,
		"source":"<a href=\"http://twitter.com\" rel=\"nofollow\">Twitter Web Client</a>",
		"isTruncated":false,
		"inReplyToStatusId":-1,
		"inReplyToUserId":-1,
		"isFavorited":false,
		"isRetweeted":false,
		"favoriteCount":0,
		"retweetCount":0,
		"isPossiblySensitive":false,
		"lang":"fr",
		"contributorsIDs":[],
		"userMentionEntities":[],
		"urlEntities":[],
		"hashtagEntities": [
			{
				"start":34,
				"end":41,
				"text":"zevent"
			}
		],
		"mediaEntities":[],
		"symbolEntities":[],
		"currentUserRetweetId":-1,
		"user": {
			"id":409479790,
			"name":"AlexMog",
			"screenName":"AlexMog_FR",
			"location":"Montpellier, France",
			"description":"MultiplayerDev @Unexpected_fr. Blockchain, AI, GameDev enthusiast. Cloud computing consultant. Consensus P2P based computation is funny.",
			"descriptionURLEntities":[],
			"isContributorsEnabled":false,
			"profileImageUrl":"http://pbs.twimg.com/profile_images/954011606089895936/bIJnJCZb_normal.jpg",
			"profileImageUrlHttps":"https://pbs.twimg.com/profile_images/954011606089895936/bIJnJCZb_normal.jpg",
			"isDefaultProfileImage":false,
			"url":"https://github.com/alexmog",
			"isProtected":false,
			"followersCount":1272,
			"profileBackgroundColor":"000000",
			"profileTextColor":"000000",
			"profileLinkColor":"666666",
			"profileSidebarFillColor":"000000",
			"profileSidebarBorderColor":"000000",
			"profileUseBackgroundImage":false,
			"isDefaultProfile":false,
			"showAllInlineMedia":false,
			"friendsCount":341,
			"createdAt":1320955295000,
			"favouritesCount":1037,
			"utcOffset":-1,
			"profileBackgroundImageUrl":"http://abs.twimg.com/images/themes/theme1/bg.png",
			"profileBackgroundImageUrlHttps":"https://abs.twimg.com/images/themes/theme1/bg.png",
			"profileBannerImageUrl":"https://pbs.twimg.com/profile_banners/409479790/1487600461",
			"profileBackgroundTiled":false,
			"lang":"fr",
			"statusesCount":4860,
			"isGeoEnabled":false,
			"isVerified":false,
			"translator":false,
			"listedCount":20,
			"isFollowRequestSent":false,
			"protected":false,
			"verified":false,
			"defaultProfile":false,
			"geoEnabled":false,
			"urlentity": {
				"start":0,
				"end":26,
				"url":"https://github.com/alexmog",
				"expandedURL":"https://github.com/alexmog",
				"displayURL":"https://github.com/alexmog",
				"text":"https://github.com/alexmog"
			},
			"profileImageURL":"http://pbs.twimg.com/profile_images/954011606089895936/bIJnJCZb_normal.jpg",
			"miniProfileImageURL":"http://pbs.twimg.com/profile_images/954011606089895936/bIJnJCZb_mini.jpg",
			"profileBackgroundImageURL":"http://abs.twimg.com/images/themes/theme1/bg.png",
			"originalProfileImageURL":"http://pbs.twimg.com/profile_images/954011606089895936/bIJnJCZb.jpg",
			"originalProfileImageURLHttps":"https://pbs.twimg.com/profile_images/954011606089895936/bIJnJCZb.jpg",
			"profileBannerRetinaURL":"https://pbs.twimg.com/profile_banners/409479790/1487600461/web_retina",
			"profileBannerMobileRetinaURL":"https://pbs.twimg.com/profile_banners/409479790/1487600461/mobile_retina",
			"profileBannerIPadURL":"https://pbs.twimg.com/profile_banners/409479790/1487600461/ipad",
			"followRequestSent":false,
			"profileBannerIPadRetinaURL":"https://pbs.twimg.com/profile_banners/409479790/1487600461/ipad_retina",
			"biggerProfileImageURL":"http://pbs.twimg.com/profile_images/954011606089895936/bIJnJCZb_bigger.jpg",
			"profileImageURLHttps":"https://pbs.twimg.com/profile_images/954011606089895936/bIJnJCZb_normal.jpg",
			"biggerProfileImageURLHttps":"https://pbs.twimg.com/profile_images/954011606089895936/bIJnJCZb_bigger.jpg",
			"profileBannerMobileURL":"https://pbs.twimg.com/profile_banners/409479790/1487600461/mobile",
			"defaultProfileImage":false,
			"miniProfileImageURLHttps":"https://pbs.twimg.com/profile_images/954011606089895936/bIJnJCZb_mini.jpg",
			"contributorsEnabled":false,
			"profileBannerURL":"https://pbs.twimg.com/profile_banners/409479790/1487600461/web",
			"accessLevel":0
		},
		"quotedStatusId":-1,
		"contributors":[],
		"possiblySensitive":false,
		"retweeted":false,
		"urlentities":[],
		"retweet":false,
		"truncated":false,
		"favorited":false,
		"retweetedByMe":false,
		"accessLevel":0
	}
}
```
NB: je n'ai listé ci-dessous que les champs les plus utiles. Vous pouvez facilement deviner à quoi servent les autres ;)  
`data` contient les données d'un tweet.  
`data.created_at` Timestamp représentant la date de création du tweet.  
`data.text` Texte du tweet.  
`data.user` Données du compte qui a tweeté.  

## Exemple JS

```javascript
<script>
var wsUri = "ws://perso.mog-creations.com:4442/";
var closed;
var websocket = null;

function sendPong() {
	if (websocket == null) return;
	websocket.send("{\"type\":\"PING\"}");
}

setInterval(sendPong, 25000); // Sending pong every 25 seconds.

function connect()
{
    console.log("Connecting...");
    if (websocket != null && websocket.readyState == websocket.OPEN)
    {
		websocket.close();
		closed = true;
    }
    // Initialisation
    websocket = new WebSocket(wsUri);
    websocket.onopen = function(evt) { onOpen(evt) };
    websocket.onclose = function(evt) { onClose(evt) };
    websocket.onmessage = function(evt) { onMessage(evt) };
    websocket.onerror = function(evt) { onError(evt) };
    closed = false;
}

function onOpen(evt)
{
    console.log("CONNECTED");
}

function onClose(evt)
{
    console.log("DISCONNECTED");
    if (!closed)
    {
		console.log("Try to reconnect in 30 sec...");
		setTimeout(connect, 30000);
    }
}

function onMessage(evt)
{
	var obj = JSON.parse(evt.data);
	console.log(obj);
	if (obj.type == "TWEET") console.log("NOUVEAU TWEET:" + obj.data.user.name + " (@" + obj.data.user.screenName + ") " + obj.data.text);
}

function onError(evt)
{
    console.log('ERROR: ' + evt.data);
}

connect();

</script>
```
