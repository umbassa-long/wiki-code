<div class="welcome">
  <div class="mist"></div>
  <div class="plant"></div>
  <p class="text">Atme tief ein. Die Kräuter der Welt warten auf dich.<br><span>Klicke, wenn du bereit bist.</span></p>
</div>

<style>
body { margin:0; background:#e8ede3; overflow:hidden; font-family:'Georgia'; text-align:center; }
.welcome { position:relative; height:100vh; display:flex; flex-direction:column; justify-content:center; align-items:center; }
.mist { position:absolute; width:120%; height:120%; background:radial-gradient(circle at 50% 50%, rgba(255,255,255,0.6), transparent 70%); animation:moveMist 8s ease-in-out infinite alternate; }
@keyframes moveMist { from { transform:translateX(-10%);} to {transform:translateX(10%);} }
.plant { width:80px; height:120px; background:url('plant.png') no-repeat center/contain; animation:grow 5s ease-out forwards; opacity:0; }
@keyframes grow { 0%{transform:scale(0.5);opacity:0;} 100%{transform:scale(1);opacity:1;} }
.text { position:relative; color:#2f3d2a; font-size:1.2em; margin-top:20px; }
.text span { font-size:0.9em; opacity:0.7; }
</style>
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTE0NjA0NjU0Nl19
-->