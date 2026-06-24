### ELD-WEBCRAWL
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Loopline</title>
<style>
  :root{
    --chrome: #3b5998;
    --chrome-dark: #2f4880;
    --page-bg: #e9ebee;
    --panel: #ffffff;
    --border: #dddfe2;
    --text: #1d2129;
    --text-muted: #65676b;
    --link: #365899;
    --like-blue: #4e69a9;
    --accent: #4267b2;
  }

  * { box-sizing: border-box; }

  body{
    margin:0;
    background: var(--page-bg);
    font-family: "Lucida Grande", Tahoma, Verdana, Arial, sans-serif;
    color: var(--text);
    font-size: 12px;
  }

  a { color: var(--link); text-decoration: none; cursor: pointer; }
  a:hover { text-decoration: underline; }

  /* ===== Top chrome ===== */
  .topbar{
    background: linear-gradient(to bottom, #4c69a5, var(--chrome) 60%, var(--chrome-dark));
    border-bottom: 1px solid #29447e;
    height: 43px;
    box-shadow: 0 1px 0 rgba(255,255,255,0.15) inset;
  }

  .topbar-inner{
    max-width: 960px;
    margin: 0 auto;
    height: 43px;
    display:flex;
    align-items:center;
    padding: 0 12px;
    gap: 14px;
  }

  .logo{
    color: #fff;
    font-size: 24px;
    font-weight: bold;
    font-family: Georgia, "Times New Roman", serif;
    letter-spacing: -0.5px;
    text-shadow: 0 1px 0 rgba(0,0,0,0.2);
  }

  .search-box{
    background: #fff;
    border-radius: 3px;
    padding: 4px 8px;
    font-size: 11px;
    color: #888;
    width: 200px;
    box-shadow: inset 0 1px 2px rgba(0,0,0,0.2);
  }

  .topbar-nav{
    margin-left: auto;
    display:flex;
    align-items:center;
    gap: 16px;
    color: #d8dfea;
    font-size: 12px;
    font-weight: bold;
  }

  .topbar-nav .pill{
    background: rgba(0,0,0,0.15);
    padding: 4px 10px;
    border-radius: 3px;
    color: #fff;
  }

  .profile-chip{
    display:flex;
    align-items:center;
    gap:6px;
    color:#fff;
  }

  .profile-chip .mini-avatar{
    width: 22px; height: 22px;
    border-radius: 2px;
    background: #c5cee0;
    border: 1px solid rgba(0,0,0,0.2);
  }

  /* ===== Layout ===== */
  .wrap{
    max-width: 960px;
    margin: 0 auto;
    padding: 20px 12px 60px;
    display:flex;
    gap: 14px;
    align-items:flex-start;
  }

  .sidebar{
    width: 180px;
    flex: 0 0 auto;
  }

  .side-panel{
    background: var(--panel);
    border: 1px solid var(--border);
    border-radius: 3px;
    padding: 10px;
    margin-bottom: 12px;
  }

  .side-panel h4{
    margin: 0 0 8px;
    font-size: 11px;
    color: var(--text-muted);
    text-transform: uppercase;
    letter-spacing: 0.03em;
    border-bottom: 1px solid var(--border);
    padding-bottom: 6px;
  }

  .side-link{
    display:flex;
    align-items:center;
    gap: 8px;
    padding: 5px 2px;
    font-size: 12px;
    color: var(--text);
  }

  .side-link .dot{
    width: 8px; height:8px; border-radius:50%;
    background: var(--accent);
    flex: 0 0 auto;
  }

  .main{
    flex: 1;
    min-width: 0;
  }

  /* ===== Page header card ===== */
  .page-card{
    background: var(--panel);
    border: 1px solid var(--border);
    border-radius: 3px;
    margin-bottom: 14px;
    overflow: hidden;
  }

  .page-banner{
    height: 70px;
    background: repeating-linear-gradient(135deg, #4267b2, #4267b2 14px, #3b5998 14px, #3b5998 28px);
  }

  .page-id{
    display:flex;
    align-items:flex-end;
    gap: 12px;
    padding: 0 14px;
    margin-top: -28px;
  }

  .page-avatar{
    width: 64px; height:64px;
    border-radius: 4px;
    background: #fceec2;
    border: 3px solid #fff;
    display:flex;
    align-items:center;
    justify-content:center;
    font-size: 26px;
  }

  .page-titles{ padding-bottom: 8px; }
  .page-titles .name{ font-size: 16px; font-weight: bold; color: var(--text); }
  .page-titles .meta{ font-size: 11px; color: var(--text-muted); }

  .page-actions{
    padding: 10px 14px;
    display:flex;
    gap: 8px;
    border-top: 1px solid var(--border);
    margin-top: 8px;
  }

  .btn{
    font-size: 11px;
    font-weight: bold;
    padding: 5px 12px;
    border-radius: 3px;
    border: 1px solid #29447e;
    background: linear-gradient(to bottom, #5b7bc4, var(--accent));
    color: #fff;
    box-shadow: 0 1px 0 rgba(255,255,255,0.3) inset;
  }

  .btn.secondary{
    background: linear-gradient(to bottom, #f5f6f7, #e9ebee);
    border: 1px solid #ccd0d5;
    color: var(--text);
    box-shadow: none;
  }

  /* ===== Post / status card ===== */
  .post-card{
    background: var(--panel);
    border: 1px solid var(--border);
    border-radius: 3px;
    margin-bottom: 14px;
  }

  .post-head{
    display:flex;
    gap: 10px;
    padding: 12px 14px 8px;
  }

  .post-avatar{
    width: 40px; height:40px;
    border-radius: 4px;
    background: #fceec2;
    flex: 0 0 auto;
    display:flex;
    align-items:center;
    justify-content:center;
    font-size: 18px;
  }

  .post-author{ font-size: 13px; font-weight: bold; color: var(--text); }
  .post-author a { color: var(--text); }
  .post-time{ font-size: 11px; color: var(--text-muted); margin-top: 1px; }
  .post-time .dot-sep{ margin: 0 3px; }

  .post-body{
    padding: 0 14px 10px;
    font-size: 13.5px;
    line-height: 1.45;
  }

  .post-body h2{
    font-size: 15px;
    margin: 4px 0 8px;
  }

  .post-body p{ margin: 0 0 10px; }

  .post-body blockquote{
    margin: 10px 0;
    padding: 6px 0 6px 12px;
    border-left: 3px solid #ccd0d5;
    color: #4b4f56;
    font-style: italic;
  }

  .post-statline{
    padding: 8px 14px;
    border-top: 1px solid var(--border);
    font-size: 11px;
    color: var(--text-muted);
    display:flex;
    justify-content: space-between;
  }

  .post-statline .likers strong{ color: var(--text); }

  .post-actions{
    display:flex;
    border-top: 1px solid var(--border);
    padding: 2px 6px;
  }

  .post-actions .action{
    flex: 1;
    text-align:center;
    padding: 6px 0;
    font-weight: bold;
    color: var(--text-muted);
    font-size: 12px;
    border-radius: 2px;
    user-select:none;
  }

  .post-actions .action:hover{ background: #f2f2f2; text-decoration:none; }
  .post-actions .action.liked{ color: var(--like-blue); }

  /* ===== Comments ===== */
  .comments-block{
    padding: 4px 14px 12px;
    border-top: 1px solid var(--border);
  }

  .comment{
    display:flex;
    gap: 8px;
    padding: 8px 0;
  }

  .c-avatar{
    width: 32px; height: 32px;
    border-radius: 4px;
    flex: 0 0 auto;
    display:flex;
    align-items:center;
    justify-content:center;
    font-size: 12px;
    font-weight: bold;
    color: #fff;
  }

  .c-body{ flex: 1; min-width:0; }

  .c-bubble{
    background: #f0f2f5;
    border-radius: 8px;
    padding: 6px 10px;
    display:inline-block;
    max-width: 100%;
  }

  .c-name{
    font-weight: bold;
    font-size: 12px;
    color: var(--text);
  }

  .c-name a{ color: var(--text); }

  .c-text{
    font-size: 12.5px;
    color: var(--text);
    margin-top: 1px;
    line-height: 1.4;
  }

  .c-meta{
    margin-top: 3px;
    font-size: 11px;
    color: var(--text-muted);
    display:flex;
    gap: 10px;
    padding-left: 10px;
  }

  .c-meta a{ font-weight: bold; color: var(--text-muted); }
  .c-meta a.liked{ color: var(--like-blue); }
  .c-meta .likecount{ color: var(--text-muted); }

  .c-replies{
    margin-left: 40px;
    margin-top: 2px;
  }

  .comment-form-row{
    display:flex;
    gap: 8px;
    padding-top: 10px;
    align-items:flex-start;
  }

  .comment-form-row .c-avatar{ background:#cfd5e3; color:#3b5998; }

  .comment-input{
    flex: 1;
    border: 1px solid #ccd0d5;
    border-radius: 14px;
    padding: 7px 12px;
    font-size: 12.5px;
    background: #f5f6f7;
    color: var(--text-muted);
  }

  footer.disclaimer{
    text-align:center;
    font-size: 11px;
    color: var(--text-muted);
    margin-top: 18px;
  }

  @media (max-width: 720px){
    .sidebar{ display:none; }
    .search-box{ width: 110px; }
  }
</style>
</head>
<body>

<div class="topbar">
  <div class="topbar-inner">
    <div class="logo">loopline</div>
    <div class="search-box">🔍 Search Loopline</div>
    <div class="topbar-nav">
      <span class="pill">Home</span>
      <span>Friends</span>
      <span>Messages</span>
      <span>Notifications</span>
      <div class="profile-chip"><div class="mini-avatar"></div> Account</div>
    </div>
  </div>
</div>

<div class="wrap">

  <div class="sidebar">
    <div class="side-panel">
      <h4>Pages you follow</h4>
      <div class="side-link"><span class="dot"></span> National Competitive Napping League</div>
      <div class="side-link"><span class="dot"></span> Pillowcraft Weekly</div>
      <div class="side-link"><span class="dot"></span> Beachvision Meditation Co.</div>
    </div>
    <div class="side-panel">
      <h4>Sponsored</h4>
      <div class="side-link"><span class="dot"></span> Memory foam, but for your soul</div>
      <div class="side-link"><span class="dot"></span> 1 weird trick for REM sleep</div>
    </div>
  </div>

  <div class="main">

    <div class="page-card">
      <div class="page-banner"></div>
      <div class="page-id">
        <div class="page-avatar">😴</div>
        <div class="page-titles">
          <div class="name">National Competitive Napping League</div>
          <div class="meta">Sports &amp; Recreation Page · 184,302 likes</div>
        </div>
      </div>
      <div class="page-actions">
        <button class="btn">👍 Like</button>
        <button class="btn secondary">Share</button>
      </div>
    </div>

    <div class="post-card">
      <div class="post-head">
        <div class="post-avatar">😴</div>
        <div>
          <div class="post-author"><a href="#">National Competitive Napping League</a></div>
          <div class="post-time">Yesterday at 6:41pm <span class="dot-sep">·</span> 🌐</div>
        </div>
      </div>
      <div class="post-body">
        <h2>Judges Strip Defending Champion of Title After "Suspiciously Alert" Re-Entry</h2>
        <p>It was supposed to be a coronation. Instead, the Tri-County Pillow Cup ended in the league's first disqualification since the infamous Snoring Microphone Incident of 2023.</p>
        <p>Two-time champion Donny Faske entered the final round a clear favorite, having posted a personal-best 41-minute sleep latency in the morning heats. But when the wake-up bell rang at the 90-minute mark, Faske allegedly sat up "too smoothly," according to lead judge Carol Pruitt, who flagged the motion as inconsistent with genuine REM disorientation.</p>
        <blockquote>"A real nap victim staggers. He just... stood up and stretched. It read rehearsed. The panel had no choice."</blockquote>
        <p>Faske's coach disputes the ruling, calling it "a hit job by people who have clearly never napped competitively in their lives." The silver medal now passes to first-time finalist Beatrix Onye, who will defend her new title at Nationals in September.</p>
      </div>
      <div class="post-statline">
        <div class="likers"><strong>Marguerite Olin</strong> and 311 others like this</div>
        <div>14 comments · 22 shares</div>
      </div>
      <div class="post-actions">
        <div class="action liked">👍 Like</div>
        <div class="action">💬 Comment</div>
        <div class="action">↗ Share</div>
      </div>

      <div class="comments-block" id="comments-block">
        <!-- comments render here -->
      </div>

      <div class="comment-form-row">
        <div class="c-avatar">YOU</div>
        <div class="comment-input">Write a comment...</div>
      </div>
    </div>

  </div>
</div>

<footer class="disclaimer">Loopline is a fictional demo site. Not affiliated with any real social network. · 2026</footer>

<script>
  // ---------------------------------------------------------------
  // Comment data — edit this array to customize names, text, times,
  // like counts, avatar colors/initials, and nested replies.
  // ---------------------------------------------------------------
  const COMMENTS = [
    {
      name: "Trent Aguilar", initials: "TA", color: "#e8a849",
      time: "23 hrs", text: "This is a witch hunt. Donny has been getting up \u201csmoothly\u201d since 2021, ask anyone. The judges just wanted a new storyline for Nationals.",
      likes: 28,
      replies: [
        { name: "Carol Pruitt", initials: "CP", color: "#4e69a9",
          time: "21 hrs", text: "I have judged 200+ naps. A trained eye knows the difference between disorientation and a guy who has clearly practiced his \u201cgroggy\u201d face in a mirror.",
          likes: 61 }
      ]
    },
    {
      name: "Beatrix Onye", initials: "BO", color: "#5cb38a",
      time: "22 hrs", text: "Honestly didn't expect to win, just kept picturing the beach like I said in every interview today. Thank you to my pillow, Gerald, for the support.",
      likes: 145,
      replies: []
    },
    {
      name: "Priya Naik", initials: "PN", color: "#c9657a",
      time: "20 hrs", text: "Genuinely cannot believe people are this invested in competitive sleeping but also I have read this article four times so who am I to judge.",
      likes: 19,
      replies: []
    },
    {
      name: "Walt Furrow", initials: "WF", color: "#7a8fc9",
      time: "19 hrs", text: "Real fans know the rules changed after 2023 specifically because of stunts like this. \u201cSuspiciously alert\u201d should just be its own penalty category.",
      likes: 9,
      replies: []
    },
    {
      name: "Donny Faske", initials: "DF", color: "#c98b3c",
      time: "18 hrs", text: "Appealing this. A man stretches when he wakes up, that's just anatomy. See you at Nationals.",
      likes: 203,
      replies: [
        { name: "Marguerite Olin", initials: "MO", color: "#a36ad1",
          time: "17 hrs", text: "Quote secured for the follow-up piece, thank you Donny.", likes: 34 }
      ]
    },
    {
      name: "Soo-jin Park", initials: "SP", color: "#3fa7a1",
      time: "16 hrs", text: "Unrelated but is anyone else's group chat just sending this article back and forth all day",
      likes: 12,
      replies: []
    },
    {
      name: "Reggie Vance", initials: "RV", color: "#d17a4a",
      time: "15 hrs", text: "Watched the replay frame by frame. He absolutely staggered first, then caught himself. Reinstate him.",
      likes: 41,
      replies: []
    },
    {
      name: "Helena Cho", initials: "HC", color: "#6a9bd8",
      time: "14 hrs", text: "Carol Pruitt has been the villain of this league since the Snoring Microphone hearings and I for one am here for it.",
      likes: 57,
      replies: []
    },
    {
      name: "Marcus Tibbetts", initials: "MT", color: "#9b8c4a",
      time: "13 hrs", text: "Gerald the pillow deserves his own sponsorship deal honestly.",
      likes: 88,
      replies: []
    },
    {
      name: "Annika Ross", initials: "AR", color: "#b25c9e",
      time: "11 hrs", text: "Can we talk about how the morning heats had a 41 minute latency and nobody questioned THAT number",
      likes: 16,
      replies: []
    },
    {
      name: "Felix Okoro", initials: "FO", color: "#4a9b6e",
      time: "10 hrs", text: "Lifelong fan, never thought I'd see a disqualification at Regionals. League's getting too competitive for its own good.",
      likes: 22,
      replies: []
    },
    {
      name: "Donna Wexler", initials: "DW", color: "#c9573f",
      time: "9 hrs", text: "My money's on Beatrix taking Nationals too. That beach visualization technique is unreal.",
      likes: 30,
      replies: []
    },
    {
      name: "Ibrahim Sall", initials: "IS", color: "#5a7a9b",
      time: "7 hrs", text: "Petition to make \u201csuspiciously alert\u201d an official scoring term in the rulebook.",
      likes: 64,
      replies: []
    },
    {
      name: "Lorraine Petty", initials: "LP", color: "#8a5ac9",
      time: "5 hrs", text: "Been to three of these tournaments live and I promise you it is so much more intense in person than this article even captures.",
      likes: 11,
      replies: []
    }
  ];

  function renderComment(c, isReply){
    const wrap = document.createElement('div');
    wrap.className = 'comment';

    const avatar = document.createElement('div');
    avatar.className = 'c-avatar';
    avatar.style.background = c.color;
    avatar.textContent = c.initials;
    wrap.appendChild(avatar);

    const body = document.createElement('div');
    body.className = 'c-body';

    const bubble = document.createElement('div');
    bubble.className = 'c-bubble';
    bubble.innerHTML = `<div class="c-name"><a href="#">${c.name}</a></div><div class="c-text">${c.text}</div>`;
    body.appendChild(bubble);

    const meta = document.createElement('div');
    meta.className = 'c-meta';
    meta.innerHTML = `
      <a href="#" class="like-link">Like</a>
      <a href="#">Reply</a>
      <span>${c.time}</span>
      <span class="likecount">${c.likes ? '👍 ' + c.likes : ''}</span>
    `;
    body.appendChild(meta);

    const likeLink = meta.querySelector('.like-link');
    const countSpan = meta.querySelector('.likecount');
    let liked = false;
    let likeCount = c.likes || 0;
    likeLink.addEventListener('click', (e) => {
      e.preventDefault();
      liked = !liked;
      likeCount += liked ? 1 : -1;
      likeLink.classList.toggle('liked', liked);
      countSpan.textContent = likeCount > 0 ? '👍 ' + likeCount : '';
    });

    wrap.appendChild(body);

    const container = document.createElement('div');
    container.appendChild(wrap);

    if (c.replies && c.replies.length){
      const repliesWrap = document.createElement('div');
      repliesWrap.className = 'c-replies';
      c.replies.forEach(r => repliesWrap.appendChild(renderComment(r, true)));
      container.appendChild(repliesWrap);
    }

    return container;
  }

  const block = document.getElementById('comments-block');
  COMMENTS.forEach(c => block.appendChild(renderComment(c, false)));

  // Top-level post Like button toggle
  document.querySelector('.post-actions .action.liked').addEventListener('click', function(e){
    this.classList.toggle('liked');
  });
</script>

</body>
</html>