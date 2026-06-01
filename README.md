<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0">
<meta http-equiv="Cache-Control" content="no-cache, no-store, must-revalidate">
<meta http-equiv="Pragma" content="no-cache">
<meta http-equiv="Expires" content="0">
<title>Daniel — Session Log v2</title>
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@tabler/icons-webfont@latest/tabler-icons.min.css">
<style>
  :root {
    --navy: #1B2A4A;
    --teal: #2A7F7F;
    --seafoam: #5BB5A2;
    --lt-teal: #E6F4F1;
    --orange: #E07B39;
    --lt-orange: #FDF0E8;
    --purple: #6B4E8A;
    --lt-purple: #F0EBF6;
    --green: #4A8C5C;
    --lt-green: #EBF5EF;
    --red: #8B2020;
    --yellow: #d4a017;
    --gray: #F5F7FA;
    --border: #E0E6ED;
    --text: #1B2A4A;
    --muted: #8A9BB0;
  }
  * { box-sizing: border-box; margin: 0; padding: 0; -webkit-tap-highlight-color: transparent; }
  body { font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif; background: #F0F4F8; color: var(--text); min-height: 100vh; }

  .header { background: var(--navy); padding: 16px 20px; display: flex; align-items: center; gap: 12px; position: sticky; top: 0; z-index: 100; }
  .header-icon { width: 38px; height: 38px; background: var(--teal); border-radius: 10px; display: flex; align-items: center; justify-content: center; flex-shrink: 0; }
  .header-icon i { color: white; font-size: 20px; }
  .header h1 { font-size: 16px; font-weight: 600; color: white; }
  .header p { font-size: 11px; color: rgba(255,255,255,0.6); margin-top: 1px; }

  .tab-bar { display: flex; background: white; border-bottom: 1px solid var(--border); position: sticky; top: 70px; z-index: 99; }
  .tab { flex: 1; padding: 12px 8px; font-size: 12px; font-weight: 500; color: var(--muted); text-align: center; cursor: pointer; border-bottom: 2px solid transparent; transition: all 0.2s; }
  .tab.active { color: var(--teal); border-bottom-color: var(--teal); }

  .content { padding: 16px; max-width: 500px; margin: 0 auto; padding-bottom: 40px; }

  .card { background: white; border-radius: 12px; padding: 16px; margin-bottom: 12px; border: 1px solid var(--border); }
  .card-title { font-size: 11px; font-weight: 600; color: var(--muted); text-transform: uppercase; letter-spacing: 0.8px; margin-bottom: 12px; display: flex; align-items: center; gap: 6px; }
  .card-title i { font-size: 14px; color: var(--teal); }

  .row2 { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; margin-bottom: 10px; }
  .row1 { margin-bottom: 10px; }

  label { font-size: 12px; color: var(--muted); display: block; margin-bottom: 4px; font-weight: 500; }
  input, select, textarea {
    width: 100%; padding: 10px 12px; border: 1px solid var(--border);
    border-radius: 8px; font-size: 14px; color: var(--text);
    background: var(--gray); font-family: inherit;
    -webkit-appearance: none; appearance: none;
  }
  input:focus, select:focus, textarea:focus { outline: none; border-color: var(--teal); background: white; }
  textarea { min-height: 80px; resize: vertical; line-height: 1.5; }

  .reg-scale { display: flex; gap: 6px; margin-top: 4px; }
  .reg-btn {
    flex: 1; height: 44px; border-radius: 8px; border: 1.5px solid var(--border);
    background: var(--gray); font-size: 16px; font-weight: 600;
    cursor: pointer; color: var(--muted); transition: all 0.15s; -webkit-appearance: none;
  }
  .reg-btn.s1 { background: var(--red); color: white; border-color: var(--red); }
  .reg-btn.s2 { background: var(--orange); color: white; border-color: var(--orange); }
  .reg-btn.s3 { background: var(--yellow); color: white; border-color: var(--yellow); }
  .reg-btn.s4 { background: var(--green); color: white; border-color: var(--green); }
  .reg-btn.s5 { background: var(--teal); color: white; border-color: var(--teal); }
  .reg-label { font-size: 11px; color: var(--muted); margin-top: 5px; text-align: center; min-height: 16px; }

  .engage-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 8px; margin-top: 6px; }
  .eng-btn {
    padding: 10px 8px; border-radius: 8px; border: 1.5px solid var(--border);
    background: var(--gray); font-size: 12px; font-weight: 500;
    cursor: pointer; text-align: center; color: var(--muted); transition: all 0.15s;
    -webkit-appearance: none;
  }
  .eng-btn.ew { background: var(--teal); color: white; border-color: var(--teal); }
  .eng-btn.ep { background: var(--seafoam); color: white; border-color: var(--seafoam); }
  .eng-btn.er { background: var(--orange); color: white; border-color: var(--orange); }
  .eng-btn.ef { background: var(--red); color: white; border-color: var(--red); }

  .beh-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 8px; margin-top: 8px; }
  .beh-chip {
    padding: 9px 8px; border-radius: 8px; border: 1.5px solid var(--border);
    background: var(--gray); font-size: 12px; font-weight: 500;
    cursor: pointer; text-align: center; color: var(--muted); transition: all 0.15s;
  }
  .beh-chip.on { background: var(--navy); color: white; border-color: var(--navy); }

  .hidden { display: none !important; }

  .submit-btn {
    width: 100%; padding: 16px; border-radius: 12px;
    background: var(--navy); color: white; font-size: 15px; font-weight: 600;
    border: none; cursor: pointer; margin-top: 4px;
    display: flex; align-items: center; justify-content: center; gap: 8px;
    -webkit-appearance: none;
  }
  .submit-btn:active { opacity: 0.85; transform: scale(0.99); }
  .submit-btn:disabled { opacity: 0.5; }

  .toast {
    position: fixed; bottom: 24px; left: 50%; transform: translateX(-50%);
    background: var(--green); color: white; padding: 12px 24px;
    border-radius: 24px; font-size: 14px; font-weight: 500;
    display: none; align-items: center; gap: 8px; z-index: 999;
    box-shadow: 0 4px 20px rgba(0,0,0,0.2); white-space: nowrap;
  }
  .toast.show { display: flex; }
  .toast.error { background: var(--red); }

  .guide-row { display: flex; align-items: flex-start; gap: 10px; padding: 10px 0; border-bottom: 1px solid var(--border); }
  .guide-row:last-child { border-bottom: none; }
  .guide-dot { width: 12px; height: 12px; border-radius: 50%; flex-shrink: 0; margin-top: 3px; }
  .guide-num { font-size: 15px; font-weight: 700; min-width: 20px; }
  .guide-title { font-size: 13px; font-weight: 600; color: var(--text); }
  .guide-desc { font-size: 12px; color: var(--muted); margin-top: 2px; line-height: 1.5; }

  .eng-guide { display: flex; flex-direction: column; gap: 8px; }
  .eng-tag { display: inline-block; padding: 3px 10px; border-radius: 6px; font-size: 11px; font-weight: 600; margin-right: 8px; }

  .setup-step { display: flex; gap: 12px; padding: 12px 0; border-bottom: 1px solid var(--border); }
  .setup-step:last-child { border-bottom: none; }
  .step-num { width: 26px; height: 26px; border-radius: 50%; background: var(--teal); color: white; font-size: 12px; font-weight: 700; display: flex; align-items: center; justify-content: center; flex-shrink: 0; margin-top: 1px; }
  .step-title { font-size: 13px; font-weight: 600; color: var(--text); margin-bottom: 4px; }
  .step-desc { font-size: 12px; color: var(--muted); line-height: 1.6; }
  .step-desc code { font-family: monospace; font-size: 11px; background: var(--gray); padding: 2px 6px; border-radius: 4px; color: var(--text); word-break: break-all; display: block; margin-top: 6px; line-height: 1.7; }

  .copy-btn {
    display: inline-flex; align-items: center; gap: 4px;
    margin-top: 8px; padding: 6px 12px; border-radius: 6px;
    border: 1px solid var(--border); background: var(--gray);
    font-size: 12px; font-weight: 500; cursor: pointer; color: var(--muted);
  }
  .copy-btn:active { background: var(--border); }

  .url-input-wrap { margin-top: 8px; }
  .url-input-wrap input { font-size: 13px; }

  .info-box { background: var(--lt-teal); border-radius: 8px; padding: 12px 14px; font-size: 12px; color: #1B4A4A; line-height: 1.6; margin-top: 8px; }

  select { background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='12' height='8' viewBox='0 0 12 8'%3E%3Cpath d='M1 1l5 5 5-5' stroke='%238A9BB0' stroke-width='1.5' fill='none' stroke-linecap='round'/%3E%3C/svg%3E"); background-repeat: no-repeat; background-position: right 12px center; padding-right: 32px; }
</style>
</head>
<body>

<div class="header">
  <div class="header-icon"><i class="ti ti-clipboard-list"></i></div>
  <div>
    <h1>Daniel — Session Log</h1>
    <p>Fill out after every activity</p>
  </div>
</div>

<div class="tab-bar">
  <div class="tab active" onclick="showTab('log')" id="tab-log">Log entry</div>
  <div class="tab" onclick="showTab('setup')" id="tab-setup">Setup</div>
  <div class="tab" onclick="showTab('guide')" id="tab-guide">Scale guide</div>
</div>

<div class="content" id="view-log">

  <div class="card">
    <div class="card-title"><i class="ti ti-calendar"></i> Session basics</div>
    <div class="row2">
      <div><label>Date</label><input type="date" id="f-date"></div>
      <div><label>Time</label><input type="time" id="f-time"></div>
    </div>
    <div class="row2">
      <div>
        <label>Your name</label>
        <select id="f-staff">
          <option value="">Select...</option>
          <option>Sammi</option><option>Anthony</option><option>Katie</option><option>Ann</option>
        </select>
      </div>
      <div>
        <label>Lead today</label>
        <select id="f-lead">
          <option value="">Select...</option>
          <option>Sammi</option><option>Anthony</option><option>Katie</option><option>Ann</option>
        </select>
      </div>
    </div>
    <div class="row1"><label>Activity name</label>
      <select id="f-activity">
        <option value="">Select activity...</option>
        <option>Morning Routine</option>
        <option>Scooter</option>
        <option>Sky Zone</option>
        <option>Jumping</option>
        <option>Lunch</option>
        <option>Lunch at Home</option>
        <option>Spelling</option>
        <option>Spelling in Oceanside</option>
        <option>Chores</option>
        <option>Horseback Riding</option>
        <option>Music Therapy</option>
        <option>Adaptive Fitness</option>
        <option>Primitive Reflexes</option>
        <option>Reading</option>
        <option>Grocery Store</option>
        <option>Harveston Park</option>
        <option>Park</option>
        <option>Morning Transition</option>
        <option>Community Outing</option>
        <option>Drive</option>
        <option>Other</option>
      </select>
    </div>
    <div class="row2">
      <div><label>Location</label><input type="text" id="f-location" placeholder="home, park..."></div>
      <div><label>Others present</label><input type="text" id="f-others" placeholder="Sammi, Anthony..."></div>
    </div>
  </div>

  <div class="card">
    <div class="card-title"><i class="ti ti-activity"></i> Regulation</div>
    <label>At the START of this activity</label>
    <div class="reg-scale">
      <button class="reg-btn" onclick="setReg('s',1,this)">1</button>
      <button class="reg-btn" onclick="setReg('s',2,this)">2</button>
      <button class="reg-btn" onclick="setReg('s',3,this)">3</button>
      <button class="reg-btn" onclick="setReg('s',4,this)">4</button>
      <button class="reg-btn" onclick="setReg('s',5,this)">5</button>
    </div>
    <div class="reg-label" id="rl-s">tap to select</div>
    <label style="margin-top:12px">At the END of this activity</label>
    <div class="reg-scale">
      <button class="reg-btn" onclick="setReg('e',1,this)">1</button>
      <button class="reg-btn" onclick="setReg('e',2,this)">2</button>
      <button class="reg-btn" onclick="setReg('e',3,this)">3</button>
      <button class="reg-btn" onclick="setReg('e',4,this)">4</button>
      <button class="reg-btn" onclick="setReg('e',5,this)">5</button>
    </div>
    <div class="reg-label" id="rl-e">tap to select</div>
  </div>

  <div class="card">
    <div class="card-title"><i class="ti ti-hand-move"></i> Engagement level</div>
    <div class="engage-grid">
      <button class="eng-btn" onclick="setEng('w',this)">✓ Willing</button>
      <button class="eng-btn" onclick="setEng('p',this)">→ Needed prompting</button>
      <button class="eng-btn" onclick="setEng('r',this)">~ Resistant</button>
      <button class="eng-btn" onclick="setEng('f',this)">✕ Refused</button>
    </div>
  </div>

  <div class="card">
    <div class="card-title"><i class="ti ti-alert-triangle"></i> Behavior episodes</div>
    <div class="row2">
      <div>
        <label>Any episodes?</label>
        <select id="f-byn" onchange="toggleBeh(this.value)">
          <option value="">Select...</option>
          <option>No</option><option>Yes</option>
        </select>
      </div>
      <div id="dur-wrap" class="hidden">
        <label>Duration (mins)</label>
        <input type="number" id="f-dur" min="0" placeholder="0">
      </div>
    </div>
    <div id="beh-detail" class="hidden">
      <label style="margin-top:8px;margin-bottom:4px">Which behaviors?</label>
      <div class="beh-grid">
        <div class="beh-chip" onclick="toggleChip(this)">Vocal escalation</div>
        <div class="beh-chip" onclick="toggleChip(this)">Verbal loop</div>
        <div class="beh-chip" onclick="toggleChip(this)">Task refusal</div>
        <div class="beh-chip" onclick="toggleChip(this)">Transition refusal</div>
        <div class="beh-chip" onclick="toggleChip(this)">SIB (self-pinching)</div>
        <div class="beh-chip" onclick="toggleChip(this)">Hair reaching</div>
        <div class="beh-chip" onclick="toggleChip(this)">Meltdown</div>
        <div class="beh-chip" onclick="toggleChip(this)">Other</div>
      </div>
      <div class="row1" style="margin-top:10px">
        <label>Antecedent — what happened right before</label>
        <textarea id="f-ante" placeholder="Use talk-to-text — what was happening, who said what..."></textarea>
      </div>
      <div class="row1">
        <label>Team response</label>
        <textarea id="f-resp" placeholder="Use talk-to-text — be specific, this is clinical data..."></textarea>
      </div>
    </div>
  </div>

  <div class="card">
    <div class="card-title"><i class="ti ti-notes"></i> Notes</div>
    <div class="row1">
      <label>Positive moments</label>
      <textarea id="f-pos" placeholder="Connection, willingness, smiles, initiations — these matter as much as the behavior data..."></textarea>
    </div>
    <div class="row1">
      <label>Additional notes (talk-to-text)</label>
      <textarea id="f-notes" placeholder="Patterns, gut feelings, team dynamics, anything worth capturing..." style="min-height:100px"></textarea>
    </div>
  </div>

  <button class="submit-btn" onclick="submit()" id="sub-btn">
    <i class="ti ti-send"></i> Save to Google Sheet
  </button>

</div>

<div class="content hidden" id="view-setup">
  <div class="card">
    <div class="card-title"><i class="ti ti-settings"></i> Connect to your Google Sheet</div>

    <div class="setup-step">
      <div class="step-num">1</div>
      <div>
        <div class="step-title">Paste your Apps Script URL</div>
        <div class="step-desc">You already have this from your deployment. Paste it below and it will be saved permanently.</div>
        <div class="url-input-wrap">
          <input type="url" id="sheet-url" placeholder="https://script.google.com/macros/s/..." oninput="saveUrl(this.value)">
        </div>
      </div>
    </div>

    <div class="setup-step">
      <div class="step-num">2</div>
      <div>
        <div class="step-title">Add column headers to your sheet</div>
        <div class="step-desc">In row 1 of your Google Sheet, paste these headers (one per cell starting at A1):
          <code>Timestamp	Date	Time	Staff	Lead	Activity	Location	Others	Reg Start	Reg End	Engagement	Behavior?	Behavior Types	Antecedent	Response	Duration	Positive Moments	Notes</code>
        </div>
        <button class="copy-btn" onclick="copyHeaders()"><i class="ti ti-copy"></i> Copy headers</button>
      </div>
    </div>

    <div class="setup-step">
      <div class="step-num">3</div>
      <div>
        <div class="step-title">Make sure your Apps Script matches this exactly</div>
        <div class="step-desc">Go to Extensions → Apps Script in your sheet and make sure this is the code:</div>
        <button class="copy-btn" onclick="copyScript()"><i class="ti ti-copy"></i> Copy the script</button>
      </div>
    </div>

    <div class="setup-step">
      <div class="step-num">4</div>
      <div>
        <div class="step-title">Save this file to your home screen</div>
        <div class="step-desc">On iPhone: open in Safari → Share → Add to Home Screen. On Android: open in Chrome → three dots → Add to Home Screen. Share the same file link with Anthony, Katie, and Ann.</div>
      </div>
    </div>

    <div class="info-box">
      <strong>Your Sheet URL is saved in this browser.</strong> Every team member needs to do the setup once on their own phone — just share this HTML file with them via Google Drive or a link.
    </div>
  </div>
</div>

<div class="content hidden" id="view-guide">
  <div class="card">
    <div class="card-title"><i class="ti ti-activity"></i> Regulation scale</div>
    <div class="guide-row">
      <div class="guide-dot" style="background:var(--red)"></div>
      <div><div class="guide-num" style="color:var(--red)">1</div></div>
      <div><div class="guide-title">Fully dysregulated</div><div class="guide-desc">Meltdown, SIB, refusing everything, inconsolable</div></div>
    </div>
    <div class="guide-row">
      <div class="guide-dot" style="background:var(--orange)"></div>
      <div><div class="guide-num" style="color:var(--orange)">2</div></div>
      <div><div class="guide-title">Elevated</div><div class="guide-desc">Agitated, avoidant, signs of distress, not engaged</div></div>
    </div>
    <div class="guide-row">
      <div class="guide-dot" style="background:var(--yellow)"></div>
      <div><div class="guide-num" style="color:var(--yellow)">3</div></div>
      <div><div class="guide-title">Neutral</div><div class="guide-desc">Manageable but not settled, neither elevated nor calm</div></div>
    </div>
    <div class="guide-row">
      <div class="guide-dot" style="background:var(--green)"></div>
      <div><div class="guide-num" style="color:var(--green)">4</div></div>
      <div><div class="guide-title">Calm</div><div class="guide-desc">Relaxed body, engaged, responsive, low avoidance</div></div>
    </div>
    <div class="guide-row">
      <div class="guide-dot" style="background:var(--teal)"></div>
      <div><div class="guide-num" style="color:var(--teal)">5</div></div>
      <div><div class="guide-title">Fully regulated</div><div class="guide-desc">Happy, initiating, enthusiastic, connected</div></div>
    </div>
  </div>

  <div class="card">
    <div class="card-title"><i class="ti ti-hand-move"></i> Engagement levels</div>
    <div class="eng-guide">
      <div class="guide-row" style="border:none;padding:8px 0">
        <span class="eng-tag" style="background:var(--teal);color:white">Willing</span>
        <span style="font-size:13px;color:var(--muted)">Participated without prompting or resistance</span>
      </div>
      <div class="guide-row" style="border:none;padding:8px 0">
        <span class="eng-tag" style="background:var(--seafoam);color:white">Prompted</span>
        <span style="font-size:13px;color:var(--muted)">Participated but needed verbal or visual prompts</span>
      </div>
      <div class="guide-row" style="border:none;padding:8px 0">
        <span class="eng-tag" style="background:var(--orange);color:white">Resistant</span>
        <span style="font-size:13px;color:var(--muted)">Showed reluctance but eventually completed</span>
      </div>
      <div class="guide-row" style="border:none;padding:8px 0">
        <span class="eng-tag" style="background:var(--red);color:white">Refused</span>
        <span style="font-size:13px;color:var(--muted)">Did not complete the activity</span>
      </div>
    </div>
  </div>

  <div class="card">
    <div class="card-title"><i class="ti ti-microphone"></i> Talk-to-text tips</div>
    <div style="display:flex;flex-direction:column;gap:0">
      <div class="guide-row"><div style="font-size:13px;color:var(--muted)">Use it in the car right after a session while details are fresh</div></div>
      <div class="guide-row"><div style="font-size:13px;color:var(--muted)">Speak naturally — accuracy matters more than grammar</div></div>
      <div class="guide-row"><div style="font-size:13px;color:var(--muted)">Narrate like you're telling a colleague what happened</div></div>
      <div class="guide-row" style="border:none"><div style="font-size:13px;color:var(--muted)">Submit before you leave your shift — details fade fast</div></div>
    </div>
  </div>
</div>

<div class="toast" id="toast"><i class="ti ti-circle-check"></i> <span id="toast-msg">Saved!</span></div>

<script>
const LABELS = ['','Fully dysregulated','Elevated','Neutral','Calm','Fully regulated'];
let rs=null, re=null, eng=null, behs=[];

function init() {
  const now = new Date();
  document.getElementById('f-date').value = now.toISOString().split('T')[0];
  document.getElementById('f-time').value = now.toTimeString().slice(0,5);
  const saved = localStorage.getItem('daniel-sheet-url') || '';
  if (saved) document.getElementById('sheet-url').value = saved;
}

function showTab(t) {
  ['log','setup','guide'].forEach(x => {
    document.getElementById('view-'+x).classList.toggle('hidden', x!==t);
    document.getElementById('tab-'+x).classList.toggle('active', x===t);
  });
}

function setReg(type, val, btn) {
  const btns = btn.parentElement.querySelectorAll('.reg-btn');
  btns.forEach(b => b.className='reg-btn');
  btn.classList.add('s'+val);
  document.getElementById('rl-'+type).textContent = val+' — '+LABELS[val];
  if(type==='s') rs=val; else re=val;
}

function setEng(code, btn) {
  document.querySelectorAll('.eng-btn').forEach(b => b.className='eng-btn');
  btn.classList.add('e'+code);
  eng = {w:'Willing',p:'Needed prompting',r:'Resistant',f:'Refused'}[code];
}

function toggleBeh(val) {
  document.getElementById('beh-detail').classList.toggle('hidden', val!=='Yes');
  document.getElementById('dur-wrap').classList.toggle('hidden', val!=='Yes');
}

function toggleChip(el) {
  el.classList.toggle('on');
  const t = el.textContent;
  behs = el.classList.contains('on') ? [...behs,t] : behs.filter(b=>b!==t);
}

function saveUrl(val) { localStorage.setItem('daniel-sheet-url', val); }

function showToast(msg, isErr) {
  const t = document.getElementById('toast');
  document.getElementById('toast-msg').textContent = msg;
  t.className = 'toast' + (isErr?' error':'') + ' show';
  setTimeout(()=>{ t.classList.remove('show'); }, 3500);
}

function copyHeaders() {
  const h = 'Timestamp\tDate\tTime\tStaff\tLead\tActivity\tLocation\tOthers\tReg Start\tReg End\tEngagement\tBehavior?\tBehavior Types\tAntecedent\tResponse\tDuration\tPositive Moments\tNotes';
  navigator.clipboard.writeText(h).then(()=>showToast('Headers copied!')).catch(()=>{});
}

function copyScript() {
  const s = `function doPost(e) {
  const sheet = SpreadsheetApp.getActiveSpreadsheet().getActiveSheet();
  const data = JSON.parse(e.postData.contents);
  sheet.appendRow([new Date(),data.date,data.time,data.staff,data.lead,
    data.activity,data.location,data.others,data.regStart,data.regEnd,
    data.engagement,data.behaviorYN,data.behaviorTypes,data.antecedent,
    data.response,data.duration,data.positive,data.notes]);
  return ContentService.createTextOutput(JSON.stringify({status:'ok'}))
    .setMimeType(ContentService.MimeType.JSON);
}`;
  navigator.clipboard.writeText(s).then(()=>showToast('Script copied!')).catch(()=>{});
}

async function submit() {
  const url = localStorage.getItem('daniel-sheet-url');
  if (!url) { showToast('Add your Sheet URL in Setup first', true); showTab('setup'); return; }

  const payload = {
    date: document.getElementById('f-date').value,
    time: document.getElementById('f-time').value,
    staff: document.getElementById('f-staff').value,
    lead: document.getElementById('f-lead').value,
    activity: document.getElementById('f-activity').value,
    location: document.getElementById('f-location').value,
    others: document.getElementById('f-others').value,
    regStart: rs||'', regEnd: re||'',
    engagement: eng||'',
    behaviorYN: document.getElementById('f-byn').value,
    behaviorTypes: behs.join(', '),
    antecedent: document.getElementById('f-ante').value,
    response: document.getElementById('f-resp').value,
    duration: document.getElementById('f-dur').value,
    positive: document.getElementById('f-pos').value,
    notes: document.getElementById('f-notes').value,
  };

  const btn = document.getElementById('sub-btn');
  btn.disabled = true;
  btn.innerHTML = '<i class="ti ti-loader"></i> Saving...';

  try {
    await fetch(url, {
      method: 'POST', mode: 'no-cors',
      body: JSON.stringify(payload),
      headers: {'Content-Type':'application/json'}
    });
    showToast('Saved to Google Sheet!');
    reset();
  } catch(err) {
    showToast('Could not save — check your URL in Setup', true);
  }

  btn.disabled = false;
  btn.innerHTML = '<i class="ti ti-send"></i> Save to Google Sheet';
}

function reset() {
  ['f-activity','f-location','f-others','f-pos','f-notes','f-ante','f-resp','f-dur'].forEach(id => {
    const el = document.getElementById(id); if(el) el.value='';
  });
  document.getElementById('f-staff').value='';
  document.getElementById('f-byn').value='';
  document.getElementById('beh-detail').classList.add('hidden');
  document.getElementById('dur-wrap').classList.add('hidden');
  document.querySelectorAll('.reg-btn').forEach(b=>b.className='reg-btn');
  document.querySelectorAll('.eng-btn').forEach(b=>b.className='eng-btn');
  document.querySelectorAll('.beh-chip').forEach(c=>c.classList.remove('on'));
  document.getElementById('rl-s').textContent='tap to select';
  document.getElementById('rl-e').textContent='tap to select';
  rs=null; re=null; eng=null; behs=[];
  const now = new Date();
  document.getElementById('f-date').value=now.toISOString().split('T')[0];
  document.getElementById('f-time').value=now.toTimeString().slice(0,5);
}

init();
</script>
</body>
</html>
