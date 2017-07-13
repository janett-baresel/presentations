$state: quality-profile$

## Quality Profile

<ul class="root-ul">
  <li class="first-lvl-li">Two possible values: <code>low</code> and <code>high</code></li>
  <li class="first-lvl-li">
    Defaults to
    <ul>
      <li><code>low</code> for IE11 and Safari</li>
      <li><code>high</code> for any other browser</li>
    </ul>
  </li>
  <li class="first-lvl-li">
    Influences
    <ul>
      <li>number of map tiles rendered</li>
      <li>scene layer detail level</li>
      <li>anti-aliasing quality</li>
    </ul>
  </li>
</ul>

<div class="code-snippet" style="width: 500px; margin-right: 100px;">
<pre><code class="lang-js">// create a new SceneView
var view = new SceneView({
  ...
  qualityProfile: "high" // or "low"
  ...
});
</code></pre>
</div>

<img src="../images/inset_low.png" style="border: none; margin: 10px; margin-top: 2px; width: 25%">
<img src="../images/inset_high.png" style="border: none; margin: 10px; margin-top: 2px; width: 25%">


<aside class="notes">
- Allows influencing the quality / performance tradeof </br>
- two settings </br>
- Defaults </br>
- should be set at SceneView creation time </br>
- influences three things </br>
- number of map tiles rendered </br>
- detail of scene layers </br>
- edge smoothing aka anti-aliasing, usually difficult to see, so I created these two cut-outs </br>
</aside>