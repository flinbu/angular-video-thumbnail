# angular-video-thumbnail
Get thumbnails, ID and embed URL from Youtube and Vimeo URL, with an Angular Factory

## To get Youtube thumbnail
Simple use the function getYoutube(url), this has a param *url*, just pass the video URL.
```
app.controller('myController', ['$scope', '$videoThumb', function ($scope, $videoThumb) {
  $scope.youtubeThumbnail = $videoThumb.getYoutube('https://www.youtube.com/watch?v=0B7lUJ8cgHs');
}]);
```
## To get Vimeo thumbnail
This is different because getVimeo(url) returns a promisse, the you have to proccess that promisse.
```
app.controller('myController', ['$scope', '$videoThumb', function ($scope, $videoThumb) {
  $videoThumb.getVimeo('https://vimeo.com/139874888').then(function (response) {
    $scope.vimeoThumbnail = response;
  });
}]);
```
## To get Youtube or Vimeo ID
This is simple, just call the function youtubeId(url) or vimeoId(url), easy!
```
app.controller('myController', ['$scope', '$videoThumb', function ($scope, $videoThumb) {
  $scope.youtubeId = $videoThumb.youtubeId('https://www.youtube.com/watch?v=0B7lUJ8cgHs');
  $scope.vimeoId = $videoThumb.vimeoId('https://vimeo.com/139874888');
}]);
```
## To get Youtube or Vimeo embed URL
This will return the URL that you can use in an iframe to embed the videos, this not will return the iframe, this functions use a $sce factory to trust in external url's because Angular block this by default.
```
app.controller('myController', ['$scope', '$videoThumb', function ($scope, $videoThumb) {
  $scope.youtubeEmbed = $videoThumb.youtubeEmbed('https://www.youtube.com/watch?v=0B7lUJ8cgHs');
  $scope.youtubeEmbed = $videoThumb.vimeoEmbed('https://vimeo.com/139874888');
}]);
```

## Off course to use this factory you need to call the file and include videoThumb module in your app file
```
<script src="https://cdnjs.cloudflare.com/ajax/libs/angular.js/1.5.8/angular.js"></script>
<script src="path/to/videoThumbFactory.js"></script>
<script src="path/to/your/app.js"></script>
```
In your app file:
```
angular.module('myApp', ['videoThumb']);
```
## thats all!
