<!DOCTYPE html>
<html lang="fa" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Arian.dev | Creative Front-End Developer</title>

<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@400;500;600;700&family=Syne:wght@600;700;800&family=Vazirmatn:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">

<style>
:root{
  --bg:#05030a;
  --bg-2:#0a0612;
  --accent:#ff4d9d;
  --accent-2:#7c5cff;
  --accent-3:#00e5ff;
  --gold:#ffb86b;
  --text:#f3efff;
  --muted:#8b84a8;
  --glass:rgba(20,12,35,.55);
  --border:rgba(124,92,255,.18);
  --border-hi:rgba(255,77,157,.35);
}

*{margin:0;padding:0;box-sizing:border-box;scroll-behavior:smooth}

html{background:var(--bg)}

body{
  font-family:"Vazirmatn",sans-serif;
  background:
    radial-gradient(ellipse 60% 40% at 15% 10%, rgba(124,92,255,.12), transparent 60%),
    radial-gradient(ellipse 50% 40% at 85% 85%, rgba(255,77,157,.10), transparent 60%),
    radial-gradient(ellipse 40% 30% at 50% 50%, rgba(0,229,255,.05), transparent 70%),
    var(--bg);
  color:var(--text);
  overflow-x:hidden;
  min-height:100vh;
}

.scroll-progress{
  position:fixed;top:0;left:0;height:2px;width:0;
  background:linear-gradient(90deg,var(--accent),var(--accent-2),var(--accent-3));
  z-index:2000;
  box-shadow:0 0 12px var(--accent);
  transition:width .1s linear;
}

.aurora{
  position:fixed;inset:0;z-index:-3;pointer-events:none;
  overflow:hidden;filter:blur(80px);opacity:.55;
}
.aurora::before,
.aurora::after{
  content:"";position:absolute;
  width:55vw;height:55vw;border-radius:50%;
  animation:auroraMove 22s ease-in-out infinite;
}
.aurora::before{
  background:radial-gradient(circle, rgba(255,77,157,.45), transparent 70%);
  top:-25%;left:-15%;
}
.aurora::after{
  background:radial-gradient(circle, rgba(124,92,255,.45), transparent 70%);
  bottom:-25%;right:-15%;
  animation-delay:-11s;
}
@keyframes auroraMove{
  0%,100%{transform:translate(0,0) scale(1)}
  50%{transform:translate(6vw,6vh) scale(1.15)}
}

.noise{
  position:fixed;inset:0;z-index:-1;pointer-events:none;opacity:.04;
  background-image:url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='.85' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)'/%3E%3C/svg%3E");
}
.vignette{
  position:fixed;inset:0;z-index:-1;pointer-events:none;
  background:radial-gradient(ellipse at center, transparent 55%, rgba(0,0,0,.55) 100%);
}

.cursor-dot,.cursor-ring{
  position:fixed;pointer-events:none;z-index:9999;border-radius:50%;
  transform:translate(-50%,-50%);will-change:transform,left,top;
}
.cursor-dot{width:6px;height:6px;background:var(--accent);box-shadow:0 0 14px var(--accent)}
.cursor-ring{
  width:36px;height:36px;border:1.5px solid rgba(255,77,157,.5);
  transition:width .25s,height .25s,border-color .25s,background .25s;
}
.cursor-ring.hover{
  width:64px;height:64px;
  border-color:var(--accent-3);
  background:rgba(0,229,255,.06);
}

nav{
  position:fixed;top:20px;left:50%;transform:translateX(-50%);
  width:min(1200px,calc(100% - 32px));height:66px;padding:0 24px;
  display:flex;justify-content:space-between;align-items:center;z-index:1000;
  background:rgba(10,6,18,.55);backdrop-filter:blur(24px) saturate(140%);
  -webkit-backdrop-filter:blur(24px) saturate(140%);
  border:1px solid var(--border);border-radius:20px;
  box-shadow:0 12px 48px rgba(0,0,0,.4), inset 0 1px 0 rgba(255,255,255,.05);
}
nav::after{
  content:"";position:absolute;left:24px;right:24px;bottom:-1px;height:1px;
  background:linear-gradient(90deg,transparent,rgba(255,77,157,.4),transparent);
  border-radius:1px;
}
.logo{
  font-family:"Syne",sans-serif;font-weight:800;font-size:19px;
  letter-spacing:-.5px;direction:ltr;
  background:linear-gradient(135deg,var(--accent),var(--accent-2),var(--accent-3));
  background-size:200% 200%;
  -webkit-background-clip:text;background-clip:text;color:transparent;
  animation:logoShift 6s ease infinite;
}
@keyframes logoShift{
  0%,100%{background-position:0% 50%}
  50%{background-position:100% 50%}
}
.logo span{color:var(--muted);font-weight:400;font-size:13px;margin-right:6px}

.nav-links{display:flex;gap:8px;list-style:none;align-items:center}
.nav-links a{
  color:#a89fc4;text-decoration:none;font-size:13px;font-weight:500;
  padding:8px 14px;border-radius:10px;transition:.25s;position:relative;
}
.nav-links a:hover{color:var(--text);background:rgba(124,92,255,.1)}
.nav-links a::after{
  content:"";position:absolute;bottom:4px;left:50%;transform:translateX(-50%);
  width:0;height:2px;background:var(--accent);transition:width .25s;border-radius:2px;
  box-shadow:0 0 10px var(--accent);
}
.nav-links a:hover::after{width:60%}

.nav-cta{
  padding:9px 20px !important;
  background:linear-gradient(135deg,var(--accent),var(--accent-2));
  background-size:200% 200%;
  color:#fff !important;font-weight:600;border-radius:11px;
  box-shadow:0 6px 24px rgba(255,77,157,.3);
  transition:.3s;
}
.nav-cta:hover{
  transform:translateY(-2px);
  box-shadow:0 10px 32px rgba(255,77,157,.5);
  background-position:100% 50%;
}
.nav-cta::after{display:none !important}

.burger{display:none;flex-direction:column;gap:5px;cursor:pointer;padding:8px}
.burger span{width:24px;height:2px;background:var(--text);border-radius:2px;transition:.3s}
.burger.open span:nth-child(1){transform:translateY(7px) rotate(45deg)}
.burger.open span:nth-child(2){opacity:0}
.burger.open span:nth-child(3){transform:translateY(-7px) rotate(-45deg)}

section{
  width:min(1200px,calc(100% - 40px));margin:auto;padding:120px 0;
  position:relative;
}
.section-head{margin-bottom:64px;position:relative}
.section-tag{
  display:inline-flex;align-items:center;gap:8px;
  font-family:"Space Grotesk",sans-serif;font-size:11px;letter-spacing:3px;
  color:var(--accent);text-transform:uppercase;margin-bottom:14px;direction:ltr;
}
.section-tag::before{
  content:"";width:24px;height:2px;background:var(--accent);border-radius:2px;
  box-shadow:0 0 8px var(--accent);
}
.section-tag::after{
  content:"";width:6px;height:6px;border-radius:50%;
  background:var(--accent);box-shadow:0 0 10px var(--accent);
  animation:tagPulse 2s ease-in-out infinite;
}
@keyframes tagPulse{
  0%,100%{opacity:1;transform:scale(1)}
  50%{opacity:.4;transform:scale(.6)}
}

.section-head h2{
  font-family:"Syne",sans-serif;font-size:clamp(34px,5.5vw,60px);
  font-weight:800;line-height:1.1;letter-spacing:-1px;
}
.section-head h2 em{
  font-style:normal;
  background:linear-gradient(135deg,var(--accent),var(--accent-2),var(--accent-3));
  background-size:200% 200%;
  -webkit-background-clip:text;background-clip:text;color:transparent;
  filter:drop-shadow(0 0 20px rgba(255,77,157,.25));
  animation:emShift 5s ease infinite;
}
@keyframes emShift{
  0%,100%{background-position:0% 50%}
  50%{background-position:100% 50%}
}
.section-head p{
  color:var(--muted);margin-top:16px;max-width:560px;line-height:1.9;font-size:14px;
}

.glass{
  background:linear-gradient(145deg,rgba(124,92,255,.06),rgba(15,10,25,.6));
  border:1px solid var(--border);backdrop-filter:blur(20px);
  -webkit-backdrop-filter:blur(20px);
  border-radius:24px;
  box-shadow:inset 0 1px 0 rgba(255,255,255,.04),0 24px 64px rgba(0,0,0,.3);
  position:relative;
}

.hero{
  min-height:100vh;display:flex;align-items:center;padding-top:140px;
  position:relative;overflow:hidden;
}
.hero-grid{display:grid;grid-template-columns:1.2fr .8fr;gap:60px;align-items:center;width:100%}

.hero-badge{
  display:inline-flex;align-items:center;gap:10px;
  padding:8px 16px;border:1px solid rgba(0,229,255,.25);border-radius:100px;
  background:rgba(0,229,255,.05);font-size:12px;color:var(--accent-3);
  margin-bottom:26px;
  box-shadow:0 0 24px rgba(0,229,255,.08);
}
.hero-badge .dot{
  width:8px;height:8px;border-radius:50%;background:var(--accent-3);
  box-shadow:0 0 12px var(--accent-3);animation:pulse 1.6s infinite;
}
@keyframes pulse{
  0%,100%{opacity:1;transform:scale(1)}
  50%{opacity:.3;transform:scale(.6)}
}

.hero h1{
  font-family:"Syne",sans-serif;font-size:clamp(42px,7vw,82px);
  font-weight:800;line-height:1.02;letter-spacing:-2.5px;margin-bottom:22px;
}
.hero h1 .grad{
  background:linear-gradient(135deg,var(--accent) 0%,var(--accent-2) 45%,var(--accent-3) 90%);
  background-size:200% 200%;
  -webkit-background-clip:text;background-clip:text;color:transparent;
  filter:drop-shadow(0 0 30px rgba(255,77,157,.25));
  animation:heroGrad 6s ease infinite;
}
@keyframes heroGrad{
  0%,100%{background-position:0% 50%}
  50%{background-position:100% 50%}
}
.hero h1 .line{display:block}
.hero h1 .line.sub{
  font-size:clamp(22px,3.2vw,34px);font-weight:600;color:var(--muted);
  letter-spacing:-.5px;margin-top:10px;
}

.hero-desc{color:#a89fc4;line-height:2;max-width:520px;font-size:15px;margin-bottom:34px}
.hero-desc strong{color:var(--text);font-weight:600}

.hero-actions{display:flex;gap:14px;flex-wrap:wrap;align-items:center}
.btn{
  display:inline-flex;align-items:center;gap:9px;
  padding:14px 26px;border-radius:14px;text-decoration:none;
  font-size:14px;font-weight:600;transition:.3s;border:none;cursor:pointer;
  font-family:inherit;position:relative;overflow:hidden;
}
.btn-primary{
  background:linear-gradient(135deg,var(--accent),var(--accent-2));
  background-size:200% 200%;
  color:#fff;
  box-shadow:0 8px 30px rgba(255,77,157,.28);
}
.btn-primary::before{
  content:"";position:absolute;inset:0;
  background:linear-gradient(120deg,transparent 30%,rgba(255,255,255,.35),transparent 70%);
  transform:translateX(-100%);
  transition:transform .7s ease;
}
.btn-primary:hover::before{transform:translateX(100%)}
.btn-primary:hover{
  transform:translateY(-3px);
  box-shadow:0 14px 40px rgba(255,77,157,.45);
  background-position:100% 50%;
}
.btn-ghost{
  background:rgba(124,92,255,.08);color:var(--text);border:1px solid var(--border);
  position:relative;
}
.btn-ghost::before{
  content:"";position:absolute;inset:0;
  background:linear-gradient(120deg,transparent 30%,rgba(255,255,255,.15),transparent 70%);
  transform:translateX(-100%);
  transition:transform .7s ease;
}
.btn-ghost:hover::before{transform:translateX(100%)}
.btn-ghost:hover{
  background:rgba(124,92,255,.16);border-color:var(--accent-2);
  transform:translateY(-3px);
}

.hero-stats{
  display:flex;gap:36px;margin-top:48px;padding-top:32px;
  border-top:1px solid rgba(255,255,255,.06);
}
.stat b{
  display:block;font-family:"Syne",sans-serif;font-size:28px;font-weight:800;
  background:linear-gradient(135deg,var(--accent),var(--accent-3));
  -webkit-background-clip:text;background-clip:text;color:transparent;
  filter:drop-shadow(0 0 12px rgba(255,77,157,.2));
}
.stat span{font-size:12px;color:var(--muted)}

.hero-visual{position:relative;display:flex;justify-content:center;align-items:center}
.orb-wrap{position:relative;width:340px;height:340px}
.orb{
  position:absolute;inset:0;border-radius:50%;
  background:radial-gradient(circle at 32% 28%,#fff 0%,var(--accent) 6%,var(--accent-2) 28%,#1a0f33 60%,#05030a 78%);
  box-shadow:
    0 0 60px rgba(124,92,255,.4),
    0 0 140px rgba(255,77,157,.18),
    inset 0 0 60px rgba(0,229,255,.15);
  animation:orbFloat 6s ease-in-out infinite;
}
.orb::after{
  content:"";position:absolute;inset:20%;border-radius:50%;
  background:radial-gradient(circle at 30% 30%, rgba(255,255,255,.5), transparent 55%);
  filter:blur(18px);mix-blend-mode:screen;
  animation:orbFloat 6s ease-in-out infinite;
  animation-delay:.4s;
}
@keyframes orbFloat{
  50%{transform:translateY(-16px) scale(1.02)}
}
.orb-ring{
  position:absolute;inset:-30px;border-radius:50%;
  border:1px solid rgba(124,92,255,.35);transform:rotate(25deg);
  animation:spin 20s linear infinite;
  box-shadow:0 0 20px rgba(124,92,255,.08);
}
.orb-ring:nth-child(2){
  inset:-52px;border-color:rgba(255,77,157,.3);transform:rotate(-25deg);
  animation:spin 28s linear infinite reverse;
}
.orb-ring:nth-child(3){
  inset:-74px;border-color:rgba(0,229,255,.2);transform:rotate(60deg);
  animation:spin 36s linear infinite;
}
@keyframes spin{to{transform:rotate(385deg)}}

.orb-label{
  position:absolute;bottom:-16px;left:50%;transform:translateX(-50%);
  white-space:nowrap;padding:7px 16px;border-radius:100px;
  background:rgba(10,6,18,.85);border:1px solid var(--border);
  font-family:"Space Grotesk",sans-serif;font-size:11px;letter-spacing:2px;
  color:var(--accent-3);backdrop-filter:blur(12px);direction:ltr;
  box-shadow:0 0 24px rgba(0,229,255,.08);
}

.chip{
  position:absolute;padding:9px 14px;border-radius:12px;
  background:rgba(10,6,18,.75);border:1px solid var(--border);
  backdrop-filter:blur(12px);font-family:"Space Grotesk",sans-serif;
  font-size:11px;letter-spacing:1px;color:var(--text);direction:ltr;
  box-shadow:0 8px 24px rgba(0,0,0,.3);white-space:nowrap;
}
.chip.a{top:10%;left:-8%;animation:float1 5s ease-in-out infinite}
.chip.b{top:35%;right:-12%;animation:float2 6s ease-in-out infinite;color:var(--accent)}
.chip.c{bottom:20%;left:-10%;animation:float1 7s ease-in-out infinite .5s;color:var(--accent-3)}
@keyframes float1{50%{transform:translateY(-12px)}}
@keyframes float2{50%{transform:translateY(10px)}}

.about-grid{display:grid;grid-template-columns:.85fr 1.15fr;gap:24px}
.about-card{padding:36px;transition:.4s;overflow:hidden}
.about-card::before{
  content:"";position:absolute;top:0;right:0;width:60px;height:60px;
  border-top:1px solid rgba(255,77,157,.4);
  border-right:1px solid rgba(255,77,157,.4);
  border-top-right-radius:24px;
  opacity:0;transition:opacity .4s;
}
.about-card::after{
  content:"";position:absolute;bottom:0;left:0;width:60px;height:60px;
  border-bottom:1px solid rgba(0,229,255,.4);
  border-left:1px solid rgba(0,229,255,.4);
  border-bottom-left-radius:24px;
  opacity:0;transition:opacity .4s;
}
.about-card:hover::before,
.about-card:hover::after{opacity:1}
.about-card:hover{
  border-color:var(--border-hi);
  transform:translateY(-6px);
  box-shadow:0 25px 60px rgba(255,77,157,.08);
}

.avatar-box{
  display:flex;flex-direction:column;align-items:center;justify-content:center;
  gap:24px;min-height:380px;position:relative;overflow:hidden;text-align:center;
}
.avatar-ring{
  width:150px;height:150px;border-radius:50%;position:relative;
  background:radial-gradient(circle at 35% 30%,#fff 0%,var(--accent-3) 5%,var(--accent-2) 22%,#0a0612 60%,#05030a 80%);
  box-shadow:
    0 0 40px rgba(124,92,255,.5),
    0 0 90px rgba(0,229,255,.15);
  animation:orbFloat 5s ease-in-out infinite;
}
.avatar-ring::after{
  content:"";position:absolute;inset:-18px;border-radius:50%;
  border:1px dashed rgba(255,77,157,.4);
  animation:spin 22s linear infinite;
}
.avatar-box h3{font-family:"Syne",sans-serif;font-size:20px;font-weight:700}
.avatar-box p{color:var(--muted);font-size:12px;letter-spacing:.5px;direction:ltr}

.about-text h3{
  font-family:"Syne",sans-serif;font-size:24px;font-weight:700;margin-bottom:18px;
}
.about-text h3 span{
  color:var(--accent);
  text-shadow:0 0 20px rgba(255,77,157,.4);
}
.about-text p{color:#a89fc4;line-height:2.1;font-size:14px;margin-bottom:14px}
.about-text p strong{color:var(--text)}

.facts{
  display:grid;grid-template-columns:repeat(2,1fr);gap:12px;margin-top:26px;
}
.fact{
  padding:14px 16px;border-radius:14px;background:rgba(124,92,255,.05);
  border:1px solid var(--border);transition:.3s;position:relative;overflow:hidden;
}
.fact::before{
  content:"";position:absolute;top:0;left:-100%;width:100%;height:100%;
  background:linear-gradient(90deg,transparent,rgba(255,77,157,.1),transparent);
  transition:left .6s ease;
}
.fact:hover::before{left:100%}
.fact:hover{
  border-color:var(--accent);
  background:rgba(124,92,255,.1);
  transform:translateY(-2px);
}
.fact span{
  display:block;font-family:"Space Grotesk",sans-serif;font-size:10px;
  letter-spacing:2px;color:var(--accent-3);margin-bottom:5px;direction:ltr;
}
.fact b{font-size:13px;font-weight:600;color:var(--text)}

.skills-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:18px}
.skill-card{
  padding:26px;position:relative;overflow:hidden;transition:.4s;
}
.skill-card:hover{
  transform:translateY(-8px);
  border-color:var(--border-hi);
  box-shadow:0 25px 60px rgba(255,77,157,.1);
}
.skill-card::before{
  content:"";position:absolute;top:-40px;left:-40px;width:120px;height:120px;
  border-radius:50%;background:var(--accent);filter:blur(70px);opacity:.08;
  transition:.4s;
}
.skill-card:hover::before{opacity:.2}
.skill-ico{
  width:48px;height:48px;border-radius:14px;display:flex;align-items:center;
  justify-content:center;font-size:24px;margin-bottom:18px;
  background:linear-gradient(135deg,rgba(255,77,157,.15),rgba(124,92,255,.15));
  border:1px solid var(--border);
  transition:.35s;
}
.skill-card:hover .skill-ico{
  transform:rotate(-6deg) scale(1.05);
  box-shadow:0 0 24px rgba(255,77,157,.2);
}
.skill-card h3{
  font-family:"Space Grotesk",sans-serif;font-size:16px;font-weight:700;
  letter-spacing:.3px;margin-bottom:8px;direction:ltr;text-align:right;
}
.skill-card p{color:var(--muted);font-size:12.5px;line-height:1.8;margin-bottom:16px}

.bar{
  height:5px;border-radius:5px;background:rgba(255,255,255,.06);overflow:hidden;
  position:relative;
}
.bar::after{
  content:"";position:absolute;inset:0;
  background:linear-gradient(90deg,transparent 30%,rgba(255,255,255,.3),transparent 70%);
  transform:translateX(-100%);
  animation:barShine 3s ease infinite;
  pointer-events:none;
}
@keyframes barShine{
  0%{transform:translateX(-100%)}
  50%,100%{transform:translateX(100%)}
}
.bar i{
  display:block;height:100%;border-radius:5px;width:0;
  background:linear-gradient(90deg,var(--accent-2),var(--accent),var(--accent-3));
  transition:width 1.4s cubic-bezier(.22,1,.36,1);
  box-shadow:0 0 10px rgba(255,77,157,.3);
}
.skill-card.in .bar i{width:var(--w)}
.bar-meta{
  display:flex;justify-content:space-between;font-family:"Space Grotesk",sans-serif;
  font-size:10px;letter-spacing:1.5px;color:var(--muted);margin-top:7px;direction:ltr;
}

.projects-grid{display:grid;grid-template-columns:repeat(2,1fr);gap:22px}
.project-card{
  padding:0;overflow:hidden;position:relative;transition:.45s;
  display:flex;flex-direction:column;min-height:340px;
}
.project-card:hover{
  transform:translateY(-8px);
  border-color:var(--border-hi);
  box-shadow:0 30px 80px rgba(255,77,157,.12);
}
.project-visual{
  height:180px;position:relative;overflow:hidden;
  background:linear-gradient(135deg,rgba(255,77,157,.12),rgba(124,92,255,.12),rgba(0,229,255,.08));
  border-bottom:1px solid var(--border);
}
.project-visual::after{
  content:"";position:absolute;inset:0;
  background:linear-gradient(180deg,transparent 60%,rgba(5,3,10,.6));
  pointer-events:none;
}
.pv-glow{
  position:absolute;width:200px;height:200px;border-radius:50%;filter:blur(50px);
  top:50%;left:50%;transform:translate(-50%,-50%);opacity:.5;
  transition:.4s;
}
.project-card:hover .pv-glow{opacity:.85;transform:translate(-50%,-50%) scale(1.2)}
.project-card:nth-child(1) .pv-glow{background:var(--accent)}
.project-card:nth-child(2) .pv-glow{background:var(--accent-2)}
.project-card:nth-child(3) .pv-glow{background:var(--accent-3)}
.project-card:nth-child(4) .pv-glow{background:var(--gold)}
.pv-shape{
  position:absolute;top:50%;left:50%;transform:translate(-50%,-50%);
  width:90px;height:90px;border-radius:50%;
  background:radial-gradient(circle at 35% 30%,#fff,var(--accent-2) 12%,#1a0f33 55%,#05030a 80%);
  box-shadow:0 0 40px rgba(124,92,255,.4);
  animation:orbFloat 5s ease-in-out infinite;
  transition:.5s;
}
.project-card:hover .pv-shape{transform:translate(-50%,-50%) scale(1.08) rotate(8deg)}
.pv-shape.alt{border-radius:18px;transform:translate(-50%,-50%) rotate(15deg)}
.pv-shape.alt2{border-radius:50% 20% 50% 20%}

.project-body{padding:24px;flex:1;display:flex;flex-direction:column}
.project-meta{
  display:flex;justify-content:space-between;align-items:center;margin-bottom:12px;
}
.project-meta .tag{
  font-family:"Space Grotesk",sans-serif;font-size:10px;letter-spacing:1.5px;
  padding:4px 10px;border-radius:100px;
  background:rgba(0,229,255,.1);
  color:var(--accent-3);border:1px solid rgba(0,229,255,.2);direction:ltr;
}
.project-meta .num{
  font-family:"Space Grotesk",sans-serif;font-size:11px;color:var(--muted);direction:ltr;
}
.project-body h3{
  font-family:"Syne",sans-serif;font-size:20px;font-weight:700;margin-bottom:8px;
  transition:.3s;
}
.project-card:hover .project-body h3{
  background:linear-gradient(135deg,var(--accent),var(--accent-3));
  -webkit-background-clip:text;background-clip:text;color:transparent;
}
.project-body p{color:var(--muted);font-size:13px;line-height:1.85;flex:1}
.project-link{
  display:inline-flex;align-items:center;gap:6px;margin-top:16px;
  color:var(--accent);text-decoration:none;font-size:13px;font-weight:600;
  transition:.25s;width:fit-content;
}
.project-link:hover{gap:12px;color:var(--accent-3)}

.timeline{position:relative;padding-right:30px}
.timeline::before{
  content:"";position:absolute;right:8px;top:0;bottom:0;width:2px;
  background:linear-gradient(180deg,var(--accent),var(--accent-2),transparent);
  box-shadow:0 0 12px rgba(255,77,157,.3);
}
.tl-item{position:relative;padding:0 34px 36px 0}
.tl-item::before{
  content:"";position:absolute;right:0;top:4px;width:18px;height:18px;
  border-radius:50%;background:var(--bg);border:2px solid var(--accent);
  box-shadow:0 0 16px rgba(255,77,157,.5);
  animation:tlPulse 3s ease-in-out infinite;
}
@keyframes tlPulse{
  0%,100%{box-shadow:0 0 16px rgba(255,77,157,.5)}
  50%{box-shadow:0 0 28px rgba(255,77,157,.9),0 0 6px rgba(255,77,157,1)}
}
.tl-item .year{
  font-family:"Space Grotesk",sans-serif;font-size:11px;letter-spacing:2px;
  color:var(--accent-3);margin-bottom:6px;direction:ltr;
}
.tl-item h4{font-family:"Syne",sans-serif;font-size:17px;font-weight:700;margin-bottom:6px}
.tl-item p{color:var(--muted);font-size:13px;line-height:1.8}

.contact-wrap{
  padding:70px 40px;text-align:center;position:relative;overflow:hidden;
}
.contact-wrap::before{
  content:"";position:absolute;width:400px;height:400px;border-radius:50%;
  background:var(--accent-2);filter:blur(120px);opacity:.12;
  top:-150px;left:50%;transform:translateX(-50%);
}
.contact-wrap::after{
  content:"";position:absolute;width:300px;height:300px;border-radius:50%;
  background:var(--accent);filter:blur(120px);opacity:.1;
  bottom:-150px;right:10%;
  animation:orbFloat 8s ease-in-out infinite;
}
.contact-wrap h2{
  font-family:"Syne",sans-serif;font-size:clamp(32px,5vw,56px);
  font-weight:800;letter-spacing:-1.5px;margin-bottom:16px;position:relative;
}
.contact-wrap h2 span{
  background:linear-gradient(135deg,var(--accent),var(--accent-3));
  background-size:200% 200%;
  -webkit-background-clip:text;background-clip:text;color:transparent;
  filter:drop-shadow(0 0 20px rgba(0,229,255,.3));
  animation:heroGrad 5s ease infinite;
}
.contact-wrap p{color:var(--muted);margin-bottom:32px;position:relative}
.contact-actions{display:flex;gap:14px;justify-content:center;flex-wrap:wrap;position:relative}

.socials{
  display:flex;gap:12px;justify-content:center;margin-top:34px;position:relative;
}
.socials a{
  width:44px;height:44px;border-radius:12px;display:flex;align-items:center;
  justify-content:center;background:rgba(124,92,255,.08);border:1px solid var(--border);
  color:var(--muted);text-decoration:none;font-size:18px;
  transition:.3s cubic-bezier(.22,1,.36,1);
}
.socials a:hover{
  color:var(--accent);border-color:var(--accent);
  transform:translateY(-4px) rotate(-8deg);
  box-shadow:0 10px 24px rgba(255,77,157,.25);
}

footer{
  padding:40px 24px;border-top:1px solid rgba(255,255,255,.05);
  text-align:center;color:#5c5473;font-size:12px;
  position:relative;
}
footer::before{
  content:"";position:absolute;top:0;left:50%;transform:translateX(-50%);
  width:200px;height:1px;
  background:linear-gradient(90deg,transparent,var(--accent),transparent);
}
footer strong{
  font-family:"Syne",sans-serif;color:var(--accent);direction:ltr;display:inline-block;
}

.reveal{
  opacity:0;transform:translateY(40px);
  transition:opacity .8s cubic-bezier(.22,1,.36,1),transform .8s cubic-bezier(.22,1,.36,1);
}
.reveal.in{opacity:1;transform:translateY(0)}

@media(max-width:960px){
  .hero-grid{grid-template-columns:1fr;gap:50px;text-align:center}
  .hero-desc{margin-inline:auto}
  .hero-actions,.hero-stats{justify-content:center}
  .hero-stats{justify-content:center;flex-wrap:wrap;gap:24px}
  .hero-visual{order:-1}
  .orb-wrap{width:260px;height:260px}
  .about-grid{grid-template-columns:1fr}
  .skills-grid{grid-template-columns:1fr 1fr}
  .projects-grid{grid-template-columns:1fr}
  .nav-links{display:none;position:absolute;top:74px;left:0;right:0;
    flex-direction:column;background:rgba(10,6,18,.97);padding:20px;
    border-radius:20px;border:1px solid var(--border);gap:6px;
    backdrop-filter:blur(24px);}
  .nav-links.open{display:flex}
  .nav-links a{padding:12px;width:100%}
  .burger{display:flex}
}

@media(max-width:560px){
  section{padding:90px 0}
  .skills-grid{grid-template-columns:1fr}
  .facts{grid-template-columns:1fr}
  .cursor-dot,.cursor-ring{display:none}
  .contact-wrap{padding:50px 24px}
  .chip{display:none}
  .aurora{filter:blur(60px);opacity:.4}
}
</style>
</head>

<body>

<div class="scroll-progress" id="scrollProgress"></div>
<div class="aurora"></div>
<div class="noise"></div>
<div class="vignette"></div>

<div class="cursor-dot"></div>
<div class="cursor-ring"></div>

<nav>
  <div class="logo">abolfazl-baghbani<span></span></div>
  <ul class="nav-links" id="navLinks">
    <li><a href="#home">خانه</a></li>
    <li><a href="#about">درباره</a></li>
    <li><a href="#skills">مهارت‌ها</a></li>
    <li><a href="#projects">پروژه‌ها</a></li>
    <li><a href="#contact" class="nav-cta">تماس</a></li>
  </ul>
  <div class="burger" id="burger">
    <span></span><span></span><span></span>
  </div>
</nav>

<section class="hero" id="home">
  <div class="hero-grid">

    <div class="hero-content">
      <div class="hero-badge">
        <span class="dot"></span>
        آماده همکاری روی پروژه‌های جدید
      </div>

      <h1>
        <span class="line">سلام، من ابوالفضلم</span>
        <span class="line grad">Freelance Web Developer</span>
        <span class="line sub"> Programmer &</span>
      </h1>

      <p class="hero-desc">
        توسعه‌دهنده فرانت‌اند با <strong>3 سال</strong> تجربه در ساخت رابط‌های کاربری مدرن،
        سریع و تعاملی. عاشق تبدیل ایده به تجربه‌های دیجیتالی هستم که هم قشنگ کار کنن،
        هم قشنگ دیده بشن.
      </p>

      <div class="hero-actions">
        <a href="#projects" class="btn btn-primary">
          مشاهده پروژه‌ها
          <span style="font-size:16px">↗</span>
        </a>
        <a href="#contact" class="btn btn-ghost">رزومه / تماس</a>
      </div>

      <div class="hero-stats">
        <div class="stat"><b>3+</b><span>سال تجربه</span></div>
        <div class="stat"><b>10+</b><span>پروژه موفق</span></div>
        <div class="stat"><b>15</b><span>سال سن</span></div>
      </div>
    </div>

    <div class="hero-visual">
      <div class="orb-wrap">
        <div class="orb-ring"></div>
        <div class="orb-ring"></div>
        <div class="orb-ring"></div>
        <div class="orb"></div>
        <div class="orb-label">CREATIVE MODE · ON</div>
        <div class="chip a">&lt;html /&gt;</div>
        <div class="chip b">React</div>
        <div class="chip c">Three.js</div>
      </div>
    </div>

  </div>
</section>

<section id="about">
  <div class="section-head reveal">
    <div class="section-tag">01 / About</div>
    <h2>درباره <em>من</em></h2>
    <p>یه برنامه‌نویس خودآموخته که از 13 سالگی کد زدن رو شروع کرد و هنوز هم هر روز چیز جدید یاد می‌گیره.</p>
  </div>

  <div class="about-grid">
    <div class="glass about-card avatar-box reveal">
      <div class="avatar-ring"></div>
      <h3>abolfazl.baghbani</h3>
      <p>FRONT-END · UI ENGINEER</p>
    </div>

    <div class="glass about-card about-text reveal">
      <h3>سلام، من <span>ابوالفضل</span> هستم 👋</h3>
      <p>
        از وقتی یادم میاد عاشق ساختن بودم؛ اول با بازی‌ها و طراحی، بعد با کد.
        الان 3 ساله که به‌صورت جدی روی توسعه‌ی وب کار می‌کنم و تمرکزم
        روی <strong>رابط‌های کاربری سریع، تمیز و خلاقانه</strong> هست.
      </p>
      <p>
        اهل عجب شیرم، دانش اموزم و در کنار درس، به‌صورت فریلنسری
        روی پروژه‌های واقعی کار می‌کنم. بهترین لحظه‌هام وقتی‌ست که یه ایده‌ی
        مبهم رو تبدیل می‌کنم به یه تجربه‌ی دیجیتال که کاربر باهاش ارتباط می‌گیره.
      </p>

      <div class="facts">
        <div class="fact"><span>NAME</span><b>abolfazl-baghbani</b></div>
        <div class="fact"><span>ROLE</span><b>Front-End Developer</b></div>
        <div class="fact"><span>LOCATION</span><b> ajabshir , Iran</b></div>
        <div class="fact"><span>FOCUS</span><b>HTML-Pyton</b></div>
        <div class="fact"><span>EDUCATION</span><b>Computer Engineering</b></div>
        <div class="fact"><span>STATUS</span><b>Open to Work</b></div>
      </div>
    </div>
  </div>
</section>

<section id="skills">
  <div class="section-head reveal">
    <div class="section-tag">02 / Skills</div>
    <h2>چی <em>می‌دونم ?</em></h2>
    <p>ابزارهایی که هر روز باهاشون کار می‌کنم و دوستشون دارم.</p>
  </div>

  <div class="skills-grid">

    <div class="glass skill-card reveal" style="--w:100%">
      <div class="skill-ico">🌐</div>
      <h3>HTML5</h3>
      <p>ساختار معنایی، سئو و دسترس‌پذیری</p>
      <div class="bar"><i></i></div>
      <div class="bar-meta"><span>MARKUP</span><span>100%</span></div>
    </div>

    <div class="glass skill-card reveal" style="--w:30%">
      <div class="skill-ico">🎨</div>
      <h3>CSS3 / Tailwind</h3>
      <p>لِی‌اوت پیشرفته، انیمیشن و ریسپانسیو</p>
      <div class="bar"><i></i></div>
      <div class="bar-meta"><span>STYLE</span><span>30%</span></div>
    </div>

    <div class="glass skill-card reveal" style="--w:88%">
      <div class="skill-ico">⚡</div>
      <h3>JavaScript / TS</h3>
      <p>DOM، API، منطق تعاملی و بهینه‌سازی</p>
      <div class="bar"><i></i></div>
      <div class="bar-meta"><span>SCRIPT</span><span>88%</span></div>
    </div>

    <div class="glass skill-card reveal" style="--w:20%">
      <div class="skill-ico">⚛️</div>
      <h3>React / Next.js</h3>
      <p>کامپوننت، State و معماری مقیاس‌پذیر</p>
      <div class="bar"><i></i></div>
      <div class="bar-meta"><span>FRAMEWORK</span><span>20%</span></div>
    </div>

    <div class="glass skill-card reveal" style="--w:78%">
      <div class="skill-ico">🧊</div>
      <h3>Three.js / WebGL</h3>
      <p>گرافیک سه‌بعدی و تجربه‌های تعاملی</p>
      <div class="bar"><i></i></div>
      <div class="bar-meta"><span>3D</span><span>78%</span></div>
    </div>

    <div class="glass skill-card reveal" style="--w:80%">
      <div class="skill-ico">🎭</div>
      <h3>Figma / UI Design</h3>
      <p>طراحی رابط، پروتوتایپ و سیستم دیزاین</p>
      <div class="bar"><i></i></div>
      <div class="bar-meta"><span>DESIGN</span><span>80%</span></div>
    </div>

  </div>
</section>

<section id="projects">
  <div class="section-head reveal">
    <div class="section-tag">03 / Projects</div>
    <h2>کارهای <em>منتخب</em></h2>
    <p>چند نمونه از پروژه‌هایی که بیشتر از همه دوستشون دارم.</p>
  </div>

  <div class="projects-grid">

    <div class="glass project-card reveal">
      <div class="project-visual">
        <div class="pv-glow"></div>
        <div class="pv-shape"></div>
      </div>
      <div class="project-body">
        <div class="project-meta">
          <span class="tag">REACT · API</span>
          <span class="num">P_01</span>
        </div>
        <h3>داشبورد تحلیل داده</h3>
        <p>یک پنل مدیریتی تعاملی با نمودارهای زنده، فیلترهای پیشرفته و طراحی تم تاریک.</p>
        <a href="#" class="project-link">مشاهده پروژه <span>→</span></a>
      </div>
    </div>

    <div class="glass project-card reveal">
      <div class="project-visual">
        <div class="pv-glow"></div>
        <div class="pv-shape alt"></div>
      </div>
      <div class="project-body">
        <div class="project-meta">
          <span class="tag">THREE.JS · GLSL</span>
          <span class="num">P_02</span>
        </div>
        <h3>لندینگ سه‌بعدی محصول</h3>
        <p>صفحه‌ی معرفی یک گجت با مدل سه‌بعدی تعاملی، افکت‌های شیدر و اسکرول سینمایی.</p>
        <a href="#" class="project-link">مشاهده پروژه <span>→</span></a>
      </div>
    </div>

    <div class="glass project-card reveal">
      <div class="project-visual">
        <div class="pv-glow"></div>
        <div class="pv-shape alt2"></div>
      </div>
      <div class="project-body">
        <div class="project-meta">
          <span class="tag">NEXT.JS · STRIPE</span>
          <span class="num">P_03</span>
        </div>
        <h3>فروشگاه آنلاین مینیمال</h3>
        <p>یک ای‌کامرس سریع با معماری SSR، سبد خرید تعاملی و پرداخت امن.</p>
        <a href="#" class="project-link">مشاهده پروژه <span>→</span></a>
      </div>
    </div>

    <div class="glass project-card reveal">
      <div class="project-visual">
        <div class="pv-glow"></div>
        <div class="pv-shape"></div>
      </div>
      <div class="project-body">
        <div class="project-meta">
          <span class="tag">UI · DESIGN</span>
          <span class="num">P_04</span>
        </div>
        <h3>سیستم طراحی اختصاصی</h3>
        <p>مجموعه‌ای از کامپوننت‌ها، توکن‌های رنگ و راهنمای استایل برای تیم محصول.</p>
        <a href="#" class="project-link">مشاهده پروژه <span>→</span></a>
      </div>
    </div>

  </div>
</section>

<section id="timeline">
  <div class="section-head reveal">
    <div class="section-tag">04 / Journey</div>
    <h2>مسیر <em>من</em></h2>
    <p>از اولین خط کد تا امروز.</p>
  </div>

  <div class="timeline reveal">
    <div class="tl-item">
      <div class="year">2024</div>
      <h4>شروع برنامه‌نویسی</h4>
      <p>با HTML/CSS شروع کردم و اولین لندینگ‌پیج‌هام رو ساختم.</p>
    </div>
    <div class="tl-item">
      <div class="year">2025</div>
      <h4>ورود به دنیای React</h4>
      <p>اولین پروژه‌های فریلنسری با React و Next.js، همراه با طراحی UI در Figma.</p>
    </div>
    <div class="tl-item">
      <div class="year">2026</div>
      <h4>کاوش در WebGL</h4>
      <p>با Three.js و شیدرها آشنا شدم و شروع به ساختن تجربه‌های سه‌بعدی کردم.</p>
    </div>
    <div class="tl-item">
      <div class="year">2026 — NOW</div>
      <h4>همکاری‌های حرفه‌ای</h4>
      <p>همکاری با استارتاپ‌ها و تیم‌های محصول روی رابط‌های کاربری واقعی.</p>
    </div>
  </div>
</section>

<section id="contact">
  <div class="glass contact-wrap reveal">
    <div class="section-tag" style="justify-content:center">05 / Contact</div>
    <h2>بیا یه چیز <span>باحال</span> بسازیم</h2>
    <p>پروژه‌ای داری یا فقط می‌خوای سلام کنی؟ پیامت خوشحالم می‌کنه.</p>

    <div class="contact-actions">
      <a href="mailto:hello@arian.dev" class="btn btn-primary">
        ارسال ایمیل ✉️
      </a>
      <a href="#" class="btn btn-ghost">دانلود رزومه 📄</a>
    </div>

    <div class="socials">
      <a href="#" title="GitHub">🐙</a>
      <a href="#" title="LinkedIn">💼</a>
      <a href="#" title="Twitter / X">𝕏</a>
      <a href="#" title="Instagram">📸</a>
    </div>
  </div>
</section>

<footer>
  Designed & Built with ❤️ by <strong>عشق</strong> · 2026
</footer>

<script>
const progress = document.getElementById('scrollProgress');
let progressTicking = false;
window.addEventListener('scroll', () => {
  if (progressTicking) return;
  progressTicking = true;
  requestAnimationFrame(() => {
    const h = document.documentElement.scrollHeight - window.innerHeight;
    const p = h > 0 ? (window.scrollY / h) * 100 : 0;
    progress.style.width = p + '%';
    progressTicking = false;
  });
}, { passive: true });

const burger = document.getElementById('burger');
const navLinks = document.getElementById('navLinks');
burger.addEventListener('click', () => {
  burger.classList.toggle('open');
  navLinks.classList.toggle('open');
});
navLinks.querySelectorAll('a').forEach(a => {
  a.addEventListener('click', () => {
    burger.classList.remove('open');
    navLinks.classList.remove('open');
  });
});

const dot = document.querySelector('.cursor-dot');
const ring = document.querySelector('.cursor-ring');
let mx = 0, my = 0, rx = 0, ry = 0;

document.addEventListener('mousemove', e => {
  mx = e.clientX; my = e.clientY;
  dot.style.left = mx + 'px';
  dot.style.top = my + 'px';
});

function loop() {
  rx += (mx - rx) * 0.16;
  ry += (my - ry) * 0.16;
  ring.style.left = rx + 'px';
  ring.style.top = ry + 'px';
  requestAnimationFrame(loop);
}
loop();

document.querySelectorAll('a, .btn, .skill-card, .project-card, .socials a, .fact').forEach(el => {
  el.addEventListener('mouseenter', () => ring.classList.add('hover'));
  el.addEventListener('mouseleave', () => ring.classList.remove('hover'));
});

const io = new IntersectionObserver(entries => {
  entries.forEach(e => {
    if (e.isIntersecting) {
      e.target.classList.add('in');
      io.unobserve(e.target);
    }
  });
}, { threshold: 0.12 });

document.querySelectorAll('.reveal').forEach((el, i) => {
  el.style.transitionDelay = ((i % 6) * 60) + 'ms';
  io.observe(el);
});

const barIO = new IntersectionObserver(entries => {
  entries.forEach(e => {
    if (e.isIntersecting) {
      e.target.classList.add('in');
      barIO.unobserve(e.target);
    }
  });
}, { threshold: 0.3 });

document.querySelectorAll('.skill-card').forEach(el => barIO.observe(el));

const visual = document.querySelector('.hero-visual');
if (visual) {
  window.addEventListener('mousemove', e => {
    const x = (e.clientX / window.innerWidth - 0.5) * 14;
    const y = (e.clientY / window.innerHeight - 0.5) * 14;
    visual.style.transform = `translate(${x}px, ${y}px)`;
  });
}

const sections = document.querySelectorAll('section[id]');
const navA = document.querySelectorAll('.nav-links a[href^="#"]');
let navTicking = false;
window.addEventListener('scroll', () => {
  if (navTicking) return;
  navTicking = true;
  requestAnimationFrame(() => {
    let current = '';
    sections.forEach(s => {
      if (window.scrollY >= s.offsetTop - 200) current = s.id;
    });
    navA.forEach(a => {
      const active = a.getAttribute('href') === '#' + current;
      a.style.color = active ? 'var(--accent)' : '';
    });
    navTicking = false;
  });
}, { passive: true });
</script>

</body>
</html>
