---
layout: none
permalink: /Challenges/Solve-the-Wordle/Problem-statement
---
<!-- markdownlint-disable -->
<!-- <!DOCTYPE html> -->
<!-- saved from url=(0053)https://solve-wordle-game-eed510c88ff8.herokuapp.com/ -->
<html lang="en"><head><meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <!-- RENAME BELOW -->
        <meta name="description" content="Solve the Wordle">
        <title>Solve the Wordle!</title>
        <script src="./Solve the Wordle!_files/webcomponents-loader.min.js.download"></script>
        <script type="module" src="./Solve the Wordle!_files/zero-md.min.js.download"></script>
        <style>
            header {
                font-family: sans-serif;
                font-size: 20px;
                text-align: center;
                position: fixed;
                width: 100%;
                line-height: 42px;
                top: 0;
                left: 0;
                background-color: #424242;
                color: white;
            }
            body {
                box-sizing: border-box;
                min-width: 200px;
                margin: 0 auto 0 auto;
                padding: 45px;
                text-align: justify;
            }
            @media (max-width: 767px) {
                header {
                    font-size: 15px;
                }
                body {
                    padding: 15px;
                }
            }
        </style>
    <script async="" src="./Solve the Wordle!_files/marked.min.js.download"></script><script async="" data-manual="" src="./Solve the Wordle!_files/prism.min.js.download"></script></head>
    <body>
        <template shadowrootmode="open"><style class="markdown-style">:host{display:block;position:relative;contain:content;}/**
 * Minified by jsDelivr using clean-css v5.3.2.
 * Original file: /npm/github-markdown-css@2.10.0/github-markdown.css
 *
 * Do NOT use SRI with dynamically generated files! More information: https://www.jsdelivr.com/using-sri-with-dynamic-files
 */
@font-face{font-family:octicons-link;src:url(data:font/woff;charset=utf-8;base64,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) format('woff')}.markdown-body{-ms-text-size-adjust:100%;-webkit-text-size-adjust:100%;line-height:1.5;color:#24292e;font-family:-apple-system,BlinkMacSystemFont,"Segoe UI",Helvetica,Arial,sans-serif,"Apple Color Emoji","Segoe UI Emoji","Segoe UI Symbol";font-size:16px;line-height:1.5;word-wrap:break-word}.markdown-body .pl-c{color:#6a737d}.markdown-body .pl-c1,.markdown-body .pl-s .pl-v{color:#005cc5}.markdown-body .pl-e,.markdown-body .pl-en{color:#6f42c1}.markdown-body .pl-s .pl-s1,.markdown-body .pl-smi{color:#24292e}.markdown-body .pl-ent{color:#22863a}.markdown-body .pl-k{color:#d73a49}.markdown-body .pl-pds,.markdown-body .pl-s,.markdown-body .pl-s .pl-pse .pl-s1,.markdown-body .pl-sr,.markdown-body .pl-sr .pl-cce,.markdown-body .pl-sr .pl-sra,.markdown-body .pl-sr .pl-sre{color:#032f62}.markdown-body .pl-smw,.markdown-body .pl-v{color:#e36209}.markdown-body .pl-bu{color:#b31d28}.markdown-body .pl-ii{color:#fafbfc;background-color:#b31d28}.markdown-body .pl-c2{color:#fafbfc;background-color:#d73a49}.markdown-body .pl-c2::before{content:"^M"}.markdown-body .pl-sr .pl-cce{font-weight:700;color:#22863a}.markdown-body .pl-ml{color:#735c0f}.markdown-body .pl-mh,.markdown-body .pl-mh .pl-en,.markdown-body .pl-ms{font-weight:700;color:#005cc5}.markdown-body .pl-mi{font-style:italic;color:#24292e}.markdown-body .pl-mb{font-weight:700;color:#24292e}.markdown-body .pl-md{color:#b31d28;background-color:#ffeef0}.markdown-body .pl-mi1{color:#22863a;background-color:#f0fff4}.markdown-body .pl-mc{color:#e36209;background-color:#ffebda}.markdown-body .pl-mi2{color:#f6f8fa;background-color:#005cc5}.markdown-body .pl-mdr{font-weight:700;color:#6f42c1}.markdown-body .pl-ba{color:#586069}.markdown-body .pl-sg{color:#959da5}.markdown-body .pl-corl{text-decoration:underline;color:#032f62}.markdown-body .octicon{display:inline-block;vertical-align:text-top;fill:currentColor}.markdown-body a{background-color:transparent}.markdown-body a:active,.markdown-body a:hover{outline-width:0}.markdown-body strong{font-weight:inherit}.markdown-body strong{font-weight:bolder}.markdown-body h1{font-size:2em;margin:.67em 0}.markdown-body img{border-style:none}.markdown-body code,.markdown-body kbd,.markdown-body pre{font-family:monospace,monospace;font-size:1em}.markdown-body hr{box-sizing:content-box;height:0;overflow:visible}.markdown-body input{font:inherit;margin:0}.markdown-body input{overflow:visible}.markdown-body [type=checkbox]{box-sizing:border-box;padding:0}.markdown-body *{box-sizing:border-box}.markdown-body input{font-family:inherit;font-size:inherit;line-height:inherit}.markdown-body a{color:#0366d6;text-decoration:none}.markdown-body a:hover{text-decoration:underline}.markdown-body strong{font-weight:600}.markdown-body hr{height:0;margin:15px 0;overflow:hidden;background:0 0;border:0;border-bottom:1px solid #dfe2e5}.markdown-body hr::before{display:table;content:""}.markdown-body hr::after{display:table;clear:both;content:""}.markdown-body table{border-spacing:0;border-collapse:collapse}.markdown-body td,.markdown-body th{padding:0}.markdown-body h1,.markdown-body h2,.markdown-body h3,.markdown-body h4,.markdown-body h5,.markdown-body h6{margin-top:0;margin-bottom:0}.markdown-body h1{font-size:32px;font-weight:600}.markdown-body h2{font-size:24px;font-weight:600}.markdown-body h3{font-size:20px;font-weight:600}.markdown-body h4{font-size:16px;font-weight:600}.markdown-body h5{font-size:14px;font-weight:600}.markdown-body h6{font-size:12px;font-weight:600}.markdown-body p{margin-top:0;margin-bottom:10px}.markdown-body blockquote{margin:0}.markdown-body ol,.markdown-body ul{padding-left:0;margin-top:0;margin-bottom:0}.markdown-body ol ol,.markdown-body ul ol{list-style-type:lower-roman}.markdown-body ol ol ol,.markdown-body ol ul ol,.markdown-body ul ol ol,.markdown-body ul ul ol{list-style-type:lower-alpha}.markdown-body dd{margin-left:0}.markdown-body code{font-family:SFMono-Regular,Consolas,"Liberation Mono",Menlo,Courier,monospace;font-size:12px}.markdown-body pre{margin-top:0;margin-bottom:0;font-family:SFMono-Regular,Consolas,"Liberation Mono",Menlo,Courier,monospace;font-size:12px}.markdown-body .octicon{vertical-align:text-bottom}.markdown-body .pl-0{padding-left:0!important}.markdown-body .pl-1{padding-left:4px!important}.markdown-body .pl-2{padding-left:8px!important}.markdown-body .pl-3{padding-left:16px!important}.markdown-body .pl-4{padding-left:24px!important}.markdown-body .pl-5{padding-left:32px!important}.markdown-body .pl-6{padding-left:40px!important}.markdown-body::before{display:table;content:""}.markdown-body::after{display:table;clear:both;content:""}.markdown-body>:first-child{margin-top:0!important}.markdown-body>:last-child{margin-bottom:0!important}.markdown-body a:not([href]){color:inherit;text-decoration:none}.markdown-body .anchor{float:left;padding-right:4px;margin-left:-20px;line-height:1}.markdown-body .anchor:focus{outline:0}.markdown-body blockquote,.markdown-body dl,.markdown-body ol,.markdown-body p,.markdown-body pre,.markdown-body table,.markdown-body ul{margin-top:0;margin-bottom:16px}.markdown-body hr{height:.25em;padding:0;margin:24px 0;background-color:#e1e4e8;border:0}.markdown-body blockquote{padding:0 1em;color:#6a737d;border-left:.25em solid #dfe2e5}.markdown-body blockquote>:first-child{margin-top:0}.markdown-body blockquote>:last-child{margin-bottom:0}.markdown-body kbd{display:inline-block;padding:3px 5px;font-size:11px;line-height:10px;color:#444d56;vertical-align:middle;background-color:#fafbfc;border:solid 1px #c6cbd1;border-bottom-color:#959da5;border-radius:3px;box-shadow:inset 0 -1px 0 #959da5}.markdown-body h1,.markdown-body h2,.markdown-body h3,.markdown-body h4,.markdown-body h5,.markdown-body h6{margin-top:24px;margin-bottom:16px;font-weight:600;line-height:1.25}.markdown-body h1 .octicon-link,.markdown-body h2 .octicon-link,.markdown-body h3 .octicon-link,.markdown-body h4 .octicon-link,.markdown-body h5 .octicon-link,.markdown-body h6 .octicon-link{color:#1b1f23;vertical-align:middle;visibility:hidden}.markdown-body h1:hover .anchor,.markdown-body h2:hover .anchor,.markdown-body h3:hover .anchor,.markdown-body h4:hover .anchor,.markdown-body h5:hover .anchor,.markdown-body h6:hover .anchor{text-decoration:none}.markdown-body h1:hover .anchor .octicon-link,.markdown-body h2:hover .anchor .octicon-link,.markdown-body h3:hover .anchor .octicon-link,.markdown-body h4:hover .anchor .octicon-link,.markdown-body h5:hover .anchor .octicon-link,.markdown-body h6:hover .anchor .octicon-link{visibility:visible}.markdown-body h1{padding-bottom:.3em;font-size:2em;border-bottom:1px solid #eaecef}.markdown-body h2{padding-bottom:.3em;font-size:1.5em;border-bottom:1px solid #eaecef}.markdown-body h3{font-size:1.25em}.markdown-body h4{font-size:1em}.markdown-body h5{font-size:.875em}.markdown-body h6{font-size:.85em;color:#6a737d}.markdown-body ol,.markdown-body ul{padding-left:2em}.markdown-body ol ol,.markdown-body ol ul,.markdown-body ul ol,.markdown-body ul ul{margin-top:0;margin-bottom:0}.markdown-body li{word-wrap:break-all}.markdown-body li>p{margin-top:16px}.markdown-body li+li{margin-top:.25em}.markdown-body dl{padding:0}.markdown-body dl dt{padding:0;margin-top:16px;font-size:1em;font-style:italic;font-weight:600}.markdown-body dl dd{padding:0 16px;margin-bottom:16px}.markdown-body table{display:block;width:100%;overflow:auto}.markdown-body table th{font-weight:600}.markdown-body table td,.markdown-body table th{padding:6px 13px;border:1px solid #dfe2e5}.markdown-body table tr{background-color:#fff;border-top:1px solid #c6cbd1}.markdown-body table tr:nth-child(2n){background-color:#f6f8fa}.markdown-body img{max-width:100%;box-sizing:content-box;background-color:#fff}.markdown-body img[align=right]{padding-left:20px}.markdown-body img[align=left]{padding-right:20px}.markdown-body code{padding:.2em .4em;margin:0;font-size:85%;background-color:rgba(27,31,35,.05);border-radius:3px}.markdown-body pre{word-wrap:normal}.markdown-body pre>code{padding:0;margin:0;font-size:100%;word-break:normal;white-space:pre;background:0 0;border:0}.markdown-body .highlight{margin-bottom:16px}.markdown-body .highlight pre{margin-bottom:0;word-break:normal}.markdown-body .highlight pre,.markdown-body pre{padding:16px;overflow:auto;font-size:85%;line-height:1.45;background-color:#f6f8fa;border-radius:3px}.markdown-body pre code{display:inline;max-width:auto;padding:0;margin:0;overflow:visible;line-height:inherit;word-wrap:normal;background-color:transparent;border:0}.markdown-body .full-commit .btn-outline:not(:disabled):hover{color:#005cc5;border-color:#005cc5}.markdown-body kbd{display:inline-block;padding:3px 5px;font:11px SFMono-Regular,Consolas,"Liberation Mono",Menlo,Courier,monospace;line-height:10px;color:#444d56;vertical-align:middle;background-color:#fafbfc;border:solid 1px #d1d5da;border-bottom-color:#c6cbd1;border-radius:3px;box-shadow:inset 0 -1px 0 #c6cbd1}.markdown-body :checked+.radio-label{position:relative;z-index:1;border-color:#0366d6}.markdown-body .task-list-item{list-style-type:none}.markdown-body .task-list-item+.task-list-item{margin-top:3px}.markdown-body .task-list-item input{margin:0 .2em .25em -1.6em;vertical-align:middle}.markdown-body hr{border-bottom-color:#eee}
/*# sourceMappingURL=/sm/80ab6bb7f46341a19c9640e6091089491733986ca6139231b5e3060ce2b68801.map */code[class*=language-],pre[class*=language-]{color:#000;background:0 0;text-shadow:0 1px #fff;font-family:Consolas,Monaco,'Andale Mono','Ubuntu Mono',monospace;font-size:1em;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none}code[class*=language-] ::-moz-selection,code[class*=language-]::-moz-selection,pre[class*=language-] ::-moz-selection,pre[class*=language-]::-moz-selection{text-shadow:none;background:#b3d4fc}code[class*=language-] ::selection,code[class*=language-]::selection,pre[class*=language-] ::selection,pre[class*=language-]::selection{text-shadow:none;background:#b3d4fc}@media print{code[class*=language-],pre[class*=language-]{text-shadow:none}}pre[class*=language-]{padding:1em;margin:.5em 0;overflow:auto}:not(pre)>code[class*=language-],pre[class*=language-]{background:#f5f2f0}:not(pre)>code[class*=language-]{padding:.1em;border-radius:.3em;white-space:normal}.token.cdata,.token.comment,.token.doctype,.token.prolog{color:#708090}.token.punctuation{color:#999}.token.namespace{opacity:.7}.token.boolean,.token.constant,.token.deleted,.token.number,.token.property,.token.symbol,.token.tag{color:#905}.token.attr-name,.token.builtin,.token.char,.token.inserted,.token.selector,.token.string{color:#690}.language-css .token.string,.style .token.string,.token.entity,.token.operator,.token.url{color:#9a6e3a;background:hsla(0,0%,100%,.5)}.token.atrule,.token.attr-value,.token.keyword{color:#07a}.token.class-name,.token.function{color:#dd4a68}.token.important,.token.regex,.token.variable{color:#e90}.token.bold,.token.important{font-weight:700}.token.italic{font-style:italic}.token.entity{cursor:help}</style><div class="markdown-body"><h1>Solve the Wordle</h1>
<a href="{{ '/' | relative_url }}">Return to index</a><br>
<a href="{{ '/Challenges/Solve-the-Wordle/' | relative_URL }}">Return to challenge page</a>
<h2>Answer to FAQs</h2>
<ul>
<li>We have a list of English words that all appear in English dictionary, but we don't have plan to release it.</li>
<li>Please check the last section for example Guess, Answer, Feedbacks.</li>
</ul>
<p><img src="https://nytco-assets.nytimes.com/2022/01/Screen-Shot-2022-01-30-at-10.05.09-PM.png?quality=100&amp;auto=webp&amp;crop=1:2&amp;width=400" alt="wordle" width="300"></p>
<h3>Instructions</h3>
<p>Wordle is a popular online word game where players have to guess a
5-letter word in 6 attempts. After each guess, the game provides feedback
on which letters are correct, which are in the word but in the wrong position,
and which are not in the word at all.</p>
<p>Your task is to write a program that can programmatically solve Wordle puzzles.
The program should take the feedback from previous guess(es) as input and then suggest
the next best word to guess.
The program should do the opening guess as well since we won't provide any starter guess.</p>
<p>Expose a <code>POST</code> endpoint <code>/wordle-game</code> for verification</p>
<p>Expected request mime-type: <code>application/json</code>
Expected response mime-type: <code>application/json</code></p>
<h4>Game Rule</h4>
<p>Each evaluation consists of 10 games.
Each game is a single Wordle game with same rules with the popular wordle game, i.e.
max 6 guesses. We will run through loops to check if the program can solve the game
within 6 guesses.</p>
<p>However, for each <code>n</code>th guess, the <code>n</code>th character will be masked and no feedback will be provided.
The final (6th) guess will have the full feedback, not masked. If you guess correctly, then the feedback will not be masekd.</p>
<h4>Expected Input</h4>
<p>Every test case will have the following format:</p>
<ol>
<li><code>list&lt;string&gt;</code> guessHistory</li>
<li><code>list&lt;string&gt;</code> evaluationHistory</li>
</ol>
<pre>{
   "guessHistory": ["slate"], 
   "evaluationHistory": ["?-X-X"]
}
</pre>
<h4>Expected Output</h4>
<ol>
<li><code>string</code> guess</li>
</ol>
<pre>{
    "guess": "lucky"
}
</pre>
<h4>Symbols</h4>
<ol>
<li><code>O</code> (letter O) means it is in correct position (green in real game).</li>
<li><code>X</code> (letter X) means it include the letter but in wrong position (yellow in real game).</li>
<li><code>-</code> (dash) means it does not include the letter (gray in real game)</li>
<li><code>?</code> (Question mark) means the feedback is masked.</li>
</ol>
<h3>Rules/Constraints</h3>
<ol>
<li>Similar to Wordle, at max 6 guesses each game</li>
</ol>
<h3>Examples</h3>
<h4>Case: Success</h4>
<p>Full game sequence:</p>
<p>Input #1:</p>
<pre>{
   "guessHistory": [], 
   "evaluationHistory": []
}
</pre>
<p>Output #1:</p>
<pre>{
    "guess": "slate"
}
</pre>
<p>Input #2:</p>
<pre>{
   "guessHistory": ["slate"], 
   "evaluationHistory": ["?-X-X"]
}
</pre>
<p>Output #2:</p>
<pre>{
    "guess": "lucky"
}
</pre>
<p>Input #3:</p>
<pre>{
   "guessHistory": ["slate", "lucky"], 
   "evaluationHistory": ["?-X-X", "-?---"]
}
</pre>
<p>Output #3:</p>
<pre>{
    "guess": "maser"
}
</pre>
<p>Input #4:</p>
<pre>{
   "guessHistory": ["slate", "lucky", "maser"], 
   "evaluationHistory": ["?-X-X", "-?---", "-O?O-"]
}
</pre>
<p>Output #4</p>
<pre>{
    "guess": "gapes"
}
</pre>
<p>Input #5:</p>
<pre>{
   "guessHistory": ["slate", "lucky", "maser", "gapes"], 
   "evaluationHistory": ["?-X-X", "-?---", "-O?O-", "XO-?O"]
}
</pre>
<p>Output #5</p>
<pre>{
    "guess": "wages"
}
</pre>
<p>Input #6:</p>
<pre>{
   "guessHistory": ["slate", "lucky", "maser", "gapes", wages], 
   "evaluationHistory": ["?-X-X", "-?---", "-O?O-", "XO-?O", "OOOOO"]
}
</pre>
<p>The game will stop here and counted as <strong><em>success</em></strong> since guess is 5 (<code>&lt;=6</code>)</p>
<h3>Example Guess, Answer, Feedback</h3>
<p>Below example doesn't include any masked character <code>?</code> <br>
<code>GUESS</code>  <code>ANSWER</code>  <code>FEEDBACK</code> <br>
<code>HELLO</code> <code>HELLO</code>  <code>OOOOO</code>  <br>
<code>AAAAA</code> <code>BBBBB</code>  <code>-----</code>  <br>
<code>ABBBB</code> <code>CBBBB</code>  <code>-OOOO</code>  <br>
<code>AbCdE</code> <code>aBcDE</code>  <code>OOOOO</code>  <br>
<code>LEVER</code> <code>EATEN</code>  <code>-X-O-</code>  <br>
<code>EAGLE</code> <code>BAGLE</code>  <code>-OOOO</code>  <br>
<code>CHEER</code> <code>CLOSE</code>  <code>O-X--</code>  <br>
<code>CLOCK</code> <code>CLOSE</code>  <code>OOO--</code>  <br>
<code>LEAVE</code> <code>CLOSE</code>  <code>X---O</code>  <br></p>
</div></template>
    

</body></html>