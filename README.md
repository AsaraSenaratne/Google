# Adding Google Analytics for Single Page

In traditional websites, when a user navigates from one page to another, the associated HTML, Javascript, CSS etc is 
rendered each time a new page loads. In SPAs, all of the necessary code is loaded once and changed when needed in response 
to user actions. The page does not reload during the entire user session. The URLs might change but that is to give the 
perception of logical pages.

Below code segment should be given within the head section of 'index.html' file

        <script>  
          (function (i, s, o, g, r, a, m) {
            i['GoogleAnalyticsObject'] = r; i[r] = i[r] || function () {
                (i[r].q = i[r].q || []).push(arguments)
            }, i[r].l = 1 * new Date(); a = s.createElement(o),
            m = s.getElementsByTagName(o)[0]; a.async = 1; a.src = g; m.parentNode.insertBefore(a, m)
          })(window, document, 'script', '//www.google-analytics.com/analytics.js', 'ga');
          
          window.ga('create', 'UA-XXXXXXXX-X', 'auto');  
        </script>
    
Replaces 'UA-XXXXXXXX-X' with the UA-ID received from Google Analytics after registration.

Next go to 'AppController.js' file and insert the below code segment within the running function.

      $rootScope.$on('$stateChangeSuccess', function (event) {
        $window.ga('send', 'pageview', $location.path());
      });
