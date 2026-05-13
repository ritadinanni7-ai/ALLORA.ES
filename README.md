<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Allora - Joyería con Significado</title>
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@fontsource/lora@5.0.8/index.css">
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@fontsource/inter@5.0.8/index.css">
<style>
*{margin:0;padding:0;box-sizing:border-box}
:root{
--primary:#5cb89b;--primary-dark:#3a7a6a;--primary-light:#b5e8d4;
--accent:#d4c5e8;--bg:#f0f7f5;--card:rgba(255,255,255,0.75);
--text:#1a3328;--text2:#4a6b5e;--text3:#7a9a8e;
--radius:20px;--radius-sm:12px;--radius-lg:30px;
--shadow:0 4px 30px rgba(0,0,0,0.06);
--shadow-lg:0 12px 50px rgba(0,0,0,0.1);
}
html{scroll-behavior:smooth}
body{font-family:'Inter',sans-serif;background:var(--bg);color:var(--text);overflow-x:hidden;line-height:1.6}
h1,h2,h3,h4,h5{font-family:'Lora',serif;font-weight:400}

/* Background */
.bg-orbs{position:fixed;top:0;left:0;right:0;bottom:0;z-index:0;pointer-events:none;overflow:hidden}
.orb{position:absolute;border-radius:50%;filter:blur(140px);opacity:.25}
.orb-1{width:700px;height:700px;background:#b5e8d4;top:-150px;left:-150px}
.orb-2{width:500px;height:500px;background:#d4c5e8;top:30%;right:-100px}
.orb-3{width:450px;height:450px;background:#b5e8d4;bottom:5%;left:20%}

/* Content */
.content{position:relative;z-index:1}

/* Nav */
.nav-wrap{position:fixed;top:0;left:0;right:0;z-index:1000;padding:14px 32px}
.nav-bar{max-width:1280px;margin:0 auto;background:rgba(255,255,255,.82);backdrop-filter:blur(24px);-webkit-backdrop-filter:blur(24px);border-radius:60px;padding:10px 28px;display:flex;align-items:center;justify-content:space-between;box-shadow:var(--shadow);border:1px solid rgba(255,255,255,.7)}
.nav-logo{display:flex;align-items:center;gap:8px;text-decoration:none;color:var(--text)}
.nav-logo svg{width:22px;height:22px}
.nav-logo span{font-family:'Lora',serif;font-size:20px;font-weight:500}
.nav-items{display:flex;align-items:center;gap:2px;list-style:none}
.nav-btn{display:flex;align-items:center;gap:4px;padding:8px 14px;border:none;background:none;color:var(--text2);font-family:'Inter',sans-serif;font-size:13.5px;font-weight:500;cursor:pointer;border-radius:30px;transition:.3s}
.nav-btn:hover,.nav-btn.active{background:rgba(92,184,155,.12);color:var(--primary-dark)}
.nav-btn .arr{width:10px;height:10px;transition:transform .3s;fill:currentColor}
.nav-btn.active .arr{transform:rotate(180deg)}
.nav-right{display:flex;align-items:center;gap:12px}
.nav-user{display:flex;align-items:center;gap:6px;padding:6px 14px;background:rgba(92,184,155,.12);border-radius:30px;font-size:12px;font-weight:600;color:var(--primary-dark)}
.nav-user .dot{width:8px;height:8px;background:var(--primary);border-radius:50%}
.nav-map-btn{display:flex;align-items:center;gap:5px;padding:8px 14px;border:none;background:none;color:var(--text2);font-size:13px;font-weight:500;cursor:pointer;border-radius:30px;font-family:'Inter',sans-serif;transition:.3s}
.nav-map-btn:hover{background:rgba(92,184,155,.12)}

/* Dropdown */
.dd{position:absolute;top:calc(100% + 6px);left:50%;transform:translateX(-50%);min-width:200px;background:rgba(255,255,255,.92);backdrop-filter:blur(20px);border-radius:16px;padding:10px;box-shadow:var(--shadow-lg);border:1px solid rgba(255,255,255,.8);opacity:0;visibility:hidden;transform:translateX(-50%) translateY(-8px);transition:.3s cubic-bezier(.4,0,.2,1)}
.dd.show{opacity:1;visibility:visible;transform:translateX(-50%) translateY(0)}
.dd a{display:block;padding:9px 14px;color:var(--text);font-size:13.5px;text-decoration:none;border-radius:10px;transition:.2s;font-weight:500}
.dd a:hover{background:linear-gradient(135deg,rgba(181,232,212,.3),rgba(212,197,232,.3))}
.dd-overlay{position:fixed;top:0;left:0;right:0;bottom:0;z-index:999;display:none}
.dd-overlay.show{display:block}

/* Sections */
.section{padding:100px 40px 60px;max-width:1200px;margin:0 auto}
.section-title{font-family:'Lora',serif;font-size:clamp(28px,4vw,42px);color:var(--text);margin-bottom:8px}
.section-sub{font-size:15px;color:var(--text2);margin-bottom:40px;max-width:600px;line-height:1.7}
.chapter-label{font-size:11px;font-weight:600;letter-spacing:3px;text-transform:uppercase;color:var(--primary);margin-bottom:10px;display:block}

/* Hero */
.hero{min-height:100vh;display:flex;flex-direction:column;align-items:center;justify-content:center;text-align:center;padding:140px 40px 80px;position:relative}
.hero-badge{display:inline-flex;align-items:center;gap:8px;background:rgba(255,255,255,.7);backdrop-filter:blur(10px);padding:10px 24px;border-radius:50px;font-size:11px;font-weight:600;letter-spacing:2.5px;text-transform:uppercase;color:var(--primary-dark);margin-bottom:36px;border:1px solid rgba(92,184,155,.15)}
.hero-badge svg{width:13px;height:13px}
.hero-h1{font-family:'Lora',serif;font-size:clamp(36px,5.5vw,68px);color:var(--text);line-height:1.15;margin-bottom:6px}
.hero-h2{font-family:'Lora',serif;font-size:clamp(32px,4.8vw,60px);font-style:italic;color:var(--primary);line-height:1.2;margin-bottom:28px}
.hero-p{max-width:520px;font-size:16px;line-height:1.75;color:var(--text2);margin-bottom:36px}
.btn-primary{display:inline-flex;align-items:center;gap:8px;padding:16px 32px;background:linear-gradient(135deg,var(--primary),#4a9b8e);color:#fff;text-decoration:none;border-radius:50px;font-size:15px;font-weight:500;transition:.3s;border:none;cursor:pointer;box-shadow:0 8px 28px rgba(92,184,155,.3)}
.btn-primary:hover{transform:translateY(-2px);box-shadow:0 12px 38px rgba(92,184,155,.4)}
.btn-primary svg{width:16px;height:16px;transition:transform .3s}
.btn-primary:hover svg{transform:translateX(4px)}

/* Cards Grid */
.cards-3{display:grid;grid-template-columns:repeat(3,1fr);gap:22px}
.glass-card{background:var(--card);backdrop-filter:blur(14px);-webkit-backdrop-filter:blur(14px);border-radius:var(--radius);padding:36px 30px;border:1px solid rgba(255,255,255,.7);box-shadow:var(--shadow);transition:.3s}
.glass-card:hover{transform:translateY(-4px);box-shadow:var(--shadow-lg)}
.card-label{font-size:11px;font-weight:600;letter-spacing:3px;text-transform:uppercase;color:var(--primary);margin-bottom:14px}
.card-text{font-family:'Lora',serif;font-size:15px;line-height:1.75;color:var(--text)}
.card-tags{display:flex;flex-wrap:wrap;gap:8px;margin-top:16px}
.tag{padding:7px 14px;background:rgba(92,184,155,.1);border-radius:50px;font-size:12px;color:var(--primary-dark);font-weight:500}

/* Quiz */
.quiz-wrap{max-width:680px;margin:0 auto}
.quiz-card{background:var(--card);backdrop-filter:blur(14px);border-radius:var(--radius-lg);padding:44px 40px;border:1px solid rgba(255,255,255,.7);box-shadow:var(--shadow);transition:.3s}
.quiz-label{font-size:11px;font-weight:600;letter-spacing:3px;text-transform:uppercase;color:var(--primary);margin-bottom:12px;display:flex;align-items:center;gap:6px}
.quiz-progress{display:flex;gap:6px;margin-bottom:24px}
.quiz-progress .bar{flex:1;height:3px;border-radius:3px;background:rgba(92,184,155,.2);transition:.4s}
.quiz-progress .bar.done{background:var(--primary)}
.quiz-q{font-family:'Lora',serif;font-size:clamp(20px,3vw,28px);color:var(--text);margin-bottom:28px;line-height:1.4}
.quiz-opt{display:block;width:100%;padding:16px 22px;margin-bottom:10px;background:rgba(255,255,255,.6);border:1px solid rgba(255,255,255,.5);border-radius:14px;font-size:14px;color:var(--text);cursor:pointer;transition:.3s;text-align:left;font-family:'Inter',sans-serif}
.quiz-opt:hover{background:rgba(92,184,155,.08);border-color:rgba(92,184,155,.3)}
.quiz-opt.selected{background:linear-gradient(135deg,rgba(92,184,155,.15),rgba(212,197,232,.15));border-color:var(--primary)}
.quiz-opt .arr{float:right;color:var(--primary);transition:.3s}
.quiz-opt:hover .arr{transform:translateX(4px)}
.quiz-result{text-align:left}
.quiz-result h3{font-family:'Lora',serif;font-size:28px;color:var(--text);margin-bottom:4px}
.quiz-result .sub{font-style:italic;color:var(--primary);font-size:16px;margin-bottom:18px;font-family:'Lora',serif}
.quiz-result p{font-size:14px;color:var(--text2);line-height:1.7;margin-bottom:20px}
.quiz-result-boxes{display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:24px}
.quiz-rbox{padding:16px;background:rgba(255,255,255,.5);border-radius:var(--radius-sm);border:1px solid rgba(255,255,255,.5)}
.quiz-rbox .lb{font-size:10px;font-weight:600;letter-spacing:2px;text-transform:uppercase;color:var(--primary);margin-bottom:6px}
.quiz-rbox .val{font-size:13px;color:var(--text);font-weight:500}
.quiz-btns{display:flex;gap:10px}
.btn-small{padding:12px 24px;border-radius:50px;font-size:13px;font-weight:500;cursor:pointer;transition:.3s;border:none;font-family:'Inter',sans-serif}
.btn-green{background:var(--primary);color:#fff}
.btn-green:hover{transform:translateY(-2px);box-shadow:0 8px 24px rgba(92,184,155,.3)}
.btn-ghost{background:rgba(255,255,255,.6);color:var(--text2);border:1px solid rgba(255,255,255,.5)}
.btn-ghost:hover{background:rgba(255,255,255,.9)}

/* Buyer Personas */
.personas-summary{margin-top:60px;padding-top:40px;border-top:1px solid rgba(92,184,155,.14)}
.personas-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:20px}
.persona-card{background:var(--card);backdrop-filter:blur(14px);border-radius:var(--radius);padding:32px 24px;border:1px solid rgba(255,255,255,.7);box-shadow:var(--shadow);transition:.3s;text-align:center}
.persona-card:hover{transform:translateY(-4px);box-shadow:var(--shadow-lg)}
.persona-avatar{width:70px;height:70px;border-radius:50%;margin:0 auto 16px;display:flex;align-items:center;justify-content:center;font-size:28px}
.persona-card h4{font-family:'Lora',serif;font-size:20px;color:var(--text);margin-bottom:4px}
.persona-sub{font-style:italic;color:var(--primary);font-size:14px;margin-bottom:12px;font-family:'Lora',serif}
.persona-desc{font-size:13px;color:var(--text2);line-height:1.6;margin-bottom:14px}
.persona-detail{font-size:11px;color:var(--text3);line-height:1.5;text-align:left;background:rgba(92,184,155,.06);padding:12px;border-radius:10px;margin-bottom:12px}
.persona-detail strong{color:var(--primary);font-size:10px;text-transform:uppercase;letter-spacing:1px;display:block;margin-bottom:4px}
.persona-piece{font-size:13px;color:var(--primary-dark);font-weight:600;background:rgba(92,184,155,.1);padding:10px 16px;border-radius:50px;display:inline-block}

/* TAM SAM SOM */
.tam-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:20px;margin-bottom:24px}
.tam-card{background:var(--card);backdrop-filter:blur(14px);border-radius:var(--radius);padding:30px;border:1px solid rgba(255,255,255,.7);box-shadow:var(--shadow);cursor:pointer;transition:.3s;position:relative;overflow:hidden}
.tam-card::after{content:'';position:absolute;top:-50%;right:-50%;width:100%;height:100%;background:linear-gradient(135deg,rgba(92,184,155,.08),rgba(212,197,232,.08));border-radius:50%;transition:.5s}
.tam-card:hover::after,.tam-card.active::after{transform:scale(2)}
.tam-card.active{border-color:var(--primary);box-shadow:var(--shadow-lg)}
.tam-card .letter{font-family:'Lora',serif;font-size:32px;color:var(--text);margin-bottom:4px}
.tam-card .sub{font-size:10px;font-weight:600;letter-spacing:2px;text-transform:uppercase;color:var(--primary);margin-bottom:8px}
.tam-card .amount{font-family:'Lora',serif;font-size:20px;color:var(--text);margin-bottom:8px}
.tam-card .hint{font-size:12px;color:var(--text3)}
.tam-card .plus{position:absolute;top:20px;right:20px;width:28px;height:28px;border-radius:50%;background:var(--primary);color:#fff;display:flex;align-items:center;justify-content:center;font-size:16px;transition:.3s}
.tam-card.active .plus{transform:rotate(45deg)}
.tam-detail{background:var(--card);backdrop-filter:blur(14px);border-radius:var(--radius);padding:32px;border:1px solid rgba(255,255,255,.7);box-shadow:var(--shadow);margin-bottom:24px}
.tam-detail h3{font-family:'Lora',serif;font-size:24px;color:var(--text);margin-bottom:4px}
.tam-detail .lb{font-size:10px;font-weight:600;letter-spacing:2px;text-transform:uppercase;color:var(--primary);margin-bottom:12px}
.tam-detail .amount{font-family:'Lora',serif;font-size:28px;color:var(--text);margin-bottom:10px}
.tam-detail p{font-size:14px;color:var(--text2);line-height:1.7}

/* PESTEL */
.pestel-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:14px;margin-bottom:50px}
.pestel-item{background:var(--card);backdrop-filter:blur(14px);border-radius:var(--radius);padding:30px 24px;border:1px solid rgba(255,255,255,.7);box-shadow:var(--shadow);cursor:pointer;transition:.3s;text-align:center}
.pestel-item:hover,.pestel-item.active{transform:translateY(-4px);box-shadow:var(--shadow-lg)}
.pestel-item.active{background:linear-gradient(135deg,rgba(92,184,155,.06),rgba(212,197,232,.06))}
.pestel-item .big{font-family:'Lora',serif;font-size:28px;color:var(--primary);margin-bottom:4px}
.pestel-item .lbl{font-size:10px;font-weight:600;letter-spacing:2px;text-transform:uppercase;color:var(--text3)}
.pestel-detail{background:var(--card);backdrop-filter:blur(14px);border-radius:var(--radius);padding:36px;border:1px solid rgba(255,255,255,.7);box-shadow:var(--shadow);margin-bottom:50px}
.pestel-detail h3{font-size:10px;font-weight:600;letter-spacing:3px;text-transform:uppercase;color:var(--primary);margin-bottom:8px}
.pestel-detail h4{font-family:'Lora',serif;font-size:20px;color:var(--text);margin-bottom:16px}
.pestel-detail li{font-size:13.5px;color:var(--text2);margin-bottom:8px;padding-left:16px;position:relative;list-style:none}
.pestel-detail li::before{content:'';position:absolute;left:0;top:8px;width:5px;height:5px;border-radius:50%;background:var(--primary)}

/* Porter */
.porter-bar{background:var(--card);backdrop-filter:blur(14px);border-radius:var(--radius);padding:20px 28px;border:1px solid rgba(255,255,255,.7);box-shadow:var(--shadow);margin-bottom:14px}
.porter-bar .top{display:flex;justify-content:space-between;align-items:center;margin-bottom:10px}
.porter-bar .name{font-family:'Lora',serif;font-size:15px;color:var(--text)}
.porter-bar .level{font-size:11px;font-weight:600;padding:4px 12px;border-radius:50px;background:rgba(92,184,155,.1);color:var(--primary-dark)}
.porter-bar .track{height:6px;background:rgba(92,184,155,.15);border-radius:3px;overflow:hidden;margin-bottom:8px}
.porter-bar .fill{height:100%;background:linear-gradient(90deg,var(--primary),#4a9b8e);border-radius:3px;transition:.6s}
.porter-bar .desc{font-size:12.5px;color:var(--text2);line-height:1.6}

/* Competitors */
.comp-grid{display:grid;grid-template-columns:repeat(2,1fr);gap:24px;margin-bottom:50px}
.comp-card{background:var(--card);backdrop-filter:blur(14px);border-radius:var(--radius);overflow:hidden;border:1px solid rgba(255,255,255,.7);box-shadow:var(--shadow);transition:.3s}
.comp-card:hover{transform:translateY(-4px);box-shadow:var(--shadow-lg)}
.comp-browser{background:#f5f5f5;padding:8px 14px;display:flex;align-items:center;gap:6px}
.comp-browser .dots{display:flex;gap:5px}
.comp-browser .dots span{width:8px;height:8px;border-radius:50%;background:#ddd}
.comp-browser .url{flex:1;font-size:11px;color:#999;margin-left:8px}
.comp-img{width:100%;height:200px;object-fit:cover;display:block}
.comp-img-placeholder{width:100%;height:200px;background:linear-gradient(135deg,#e8f5f0,#f0e8f5);display:flex;align-items:center;justify-content:center;font-size:40px}
.comp-info{padding:20px 24px}
.comp-info h3{font-family:'Lora',serif;font-size:18px;color:var(--text);margin-bottom:4px}
.comp-info .price{font-size:13px;color:var(--primary);font-weight:600;margin-bottom:4px}
.comp-info .desc{font-size:13px;color:var(--text2);margin-bottom:10px}
.comp-info .tag{display:inline-block;padding:5px 12px;background:rgba(92,184,155,.1);border-radius:50px;font-size:11px;color:var(--primary-dark);font-weight:500}
.comp-link{float:right;font-size:12px;color:var(--primary);text-decoration:none;font-weight:500}

/* Trends */
.trends-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:16px;margin-bottom:50px}
.trend-card{background:var(--card);backdrop-filter:blur(14px);border-radius:var(--radius);padding:24px;border:1px solid rgba(255,255,255,.7);box-shadow:var(--shadow);transition:.3s}
.trend-card:hover{transform:translateY(-4px);box-shadow:var(--shadow-lg)}
.trend-card h4{font-family:'Lora',serif;font-size:15px;color:var(--text);margin-bottom:6px}
.trend-card p{font-size:12.5px;color:var(--text2);line-height:1.6}

/* BMC */
.bmc-grid{display:grid;grid-template-columns:repeat(5,1fr);grid-template-rows:auto auto auto;gap:12px;margin-bottom:50px}
.bmc-cell{background:var(--card);backdrop-filter:blur(14px);border-radius:var(--radius);padding:22px;border:1px solid rgba(255,255,255,.7);box-shadow:var(--shadow);cursor:pointer;transition:.3s;min-height:120px;display:flex;flex-direction:column;align-items:center;justify-content:center;text-align:center}
.bmc-cell:hover,.bmc-cell.active{transform:translateY(-3px);box-shadow:var(--shadow-lg)}
.bmc-cell.active{background:linear-gradient(135deg,rgba(92,184,155,.08),rgba(212,197,232,.08))}
.bmc-cell .icon{width:36px;height:36px;border-radius:10px;background:rgba(92,184,155,.1);display:flex;align-items:center;justify-content:center;margin-bottom:10px;font-size:16px}
.bmc-cell .eng{font-size:9px;font-weight:600;letter-spacing:1.5px;text-transform:uppercase;color:var(--primary);margin-bottom:4px}
.bmc-cell .sp{font-size:13px;color:var(--text);font-weight:500;line-height:1.5}
.bmc-cell.wide{grid-column:span 2}
.bmc-cell .details{display:none;font-size:12px;color:var(--text2);text-align:left;line-height:1.7;margin-top:8px;padding-top:8px;border-top:1px solid rgba(92,184,155,.1)}
.bmc-cell.active .details{display:block}

/* Value Chain */
value-chain-container{margin-bottom:50px}
.vc-wrapper{background:var(--card);backdrop-filter:blur(14px);border-radius:var(--radius);padding:36px;border:1px solid rgba(255,255,255,.7);box-shadow:var(--shadow);overflow-x:auto}
.vc-grid{display:grid;grid-template-columns:auto 1fr auto;gap:0;min-width:800px}
.vc-support-label{writing-mode:vertical-lr;transform:rotate(180deg);font-size:11px;font-weight:600;letter-spacing:2px;text-transform:uppercase;color:var(--text3);display:flex;align-items:center;justify-content:center;padding:0 12px}
.vc-primary-label{text-align:center;font-size:11px;font-weight:600;letter-spacing:2px;text-transform:uppercase;color:var(--text3);padding-top:12px;grid-column:2}
.vc-support{display:grid;grid-template-rows:repeat(4,1fr);gap:6px;padding-right:16px}
.vc-support-item{padding:14px 18px;border-radius:12px;border:1px solid;display:flex;align-items:center;gap:14px;transition:.3s;cursor:pointer}
.vc-support-item:hover{transform:translateX(4px)}
.vc-support-item.si{background:#ede9fe;border-color:#c4b5fd}.vc-support-item.rrhh{background:#d1fae5;border-color:#a7f3d0}
.vc-support-item.tech{background:#dbeafe;border-color:#93c5fd}.vc-support-item.aprov{background:#fef3c7;border-color:#fcd34d}
.vc-support-item .vc-icon{width:32px;height:32px;border-radius:8px;display:flex;align-items:center;justify-content:center;font-size:16px;flex-shrink:0}
.vc-support-item .vc-text h4{font-family:'Lora',serif;font-size:14px;color:var(--text);margin-bottom:2px}
.vc-support-item .vc-text p{font-size:11px;color:var(--text3);line-height:1.4}
.vc-primary-item{padding:14px;border-radius:12px;border:1px solid;text-align:center;transition:.3s;cursor:pointer}
.vc-primary-item:hover{transform:translateY(-3px);box-shadow:var(--shadow)}
.vc-primary-item.li{background:#d1fae5;border-color:#a7f3d0}.vc-primary-item.op{background:#dbeafe;border-color:#93c5fd}
.vc-primary-item.le{background:#ede9fe;border-color:#c4b5fd}.vc-primary-item.mk{background:#fef3c7;border-color:#fcd34d}
.vc-primary-item.ps{background:#d1fae5;border-color:#a7f3d0}
.vc-primary-item h4{font-family:'Lora',serif;font-size:13px;color:var(--text);margin-bottom:6px}
.vc-primary-item ul{list-style:none;padding:0}
.vc-primary-item li{font-size:11px;color:var(--text2);margin-bottom:3px;line-height:1.4}
.vc-arrow{display:flex;align-items:center;font-size:18px;color:var(--text3);padding:0 2px}
.vc-margin{writing-mode:vertical-lr;transform:rotate(180deg);font-size:13px;font-weight:600;color:var(--text3);background:#f5f5f0;border:1px solid #e5e5d5;border-radius:12px;display:flex;align-items:center;justify-content:center;padding:20px 10px;min-height:200px}

/* Positioning Map */
.pos-map{background:var(--card);backdrop-filter:blur(14px);border-radius:var(--radius);padding:30px;border:1px solid rgba(255,255,255,.7);box-shadow:var(--shadow);position:relative;height:420px;margin-bottom:50px}
.pos-map .axis-x{position:absolute;bottom:40px;left:40px;right:40px;height:1px;background:rgba(92,184,155,.3)}
.pos-map .axis-y{position:absolute;top:40px;bottom:40px;left:calc(50% - .5px);width:1px;background:rgba(92,184,155,.3)}
.pos-map .lbl-x1{position:absolute;bottom:14px;left:40px;font-size:10px;color:var(--text3);font-weight:500}
.pos-map .lbl-x2{position:absolute;bottom:14px;right:40px;font-size:10px;color:var(--text3);font-weight:500}
.pos-map .lbl-y1{position:absolute;top:14px;left:14px;font-size:10px;color:var(--text3);font-weight:500}
.pos-map .lbl-y2{position:absolute;bottom:50px;left:14px;font-size:10px;color:var(--text3);font-weight:500}
.pos-dot{position:absolute;width:12px;height:12px;border-radius:50%;background:var(--primary);cursor:pointer;transition:.3s}
.pos-dot:hover{transform:scale(1.5)}
.pos-dot .label{position:absolute;top:16px;left:50%;transform:translateX(-50%);white-space:nowrap;font-size:11px;font-weight:500;color:var(--text);background:rgba(255,255,255,.9);padding:3px 10px;border-radius:20px;box-shadow:0 2px 8px rgba(0,0,0,.08);font-family:'Inter',sans-serif}
.pos-dot .price{display:block;font-size:10px;color:var(--text3);font-weight:400}

/* Life Cycle */
.lifecycle-container{margin-bottom:50px}
.lc-wrapper{background:var(--card);backdrop-filter:blur(14px);border-radius:var(--radius);padding:36px;border:1px solid rgba(255,255,255,.7);box-shadow:var(--shadow)}
.lc-chart{position:relative;height:280px;margin-bottom:30px}
.lc-curve{position:absolute;bottom:40px;left:60px;right:30px;height:200px}
.lc-svg{width:100%;height:100%}
.lc-expand{display:grid;grid-template-columns:repeat(4,1fr);gap:14px;margin-top:20px}
.lc-expand-card{border-radius:16px;padding:24px 20px;border:1px solid;cursor:pointer;transition:.3s;overflow:hidden}
.lc-expand-card:hover{transform:translateY(-3px)}
.lc-expand-card.ec-intro{background:#f0fdf4;border-color:#a7f3d0}
.lc-expand-card.ec-growth{background:#fffbeb;border-color:#fcd34d}
.lc-expand-card.ec-maturity{background:#f5f3ff;border-color:#c4b5fd}
.lc-expand-card.ec-decline{background:#fef2f2;border-color:#fecaca}
.lc-expand-card h4{font-family:'Lora',serif;font-size:17px;margin-bottom:10px;display:flex;align-items:center;gap:8px}
.lc-expand-card h4 .lc-toggle{margin-left:auto;font-size:18px;transition:transform .3s}
.lc-expand-card.open h4 .lc-toggle{transform:rotate(180deg)}
.lc-expand-card .lc-items{max-height:0;overflow:hidden;transition:max-height .4s ease}
.lc-expand-card.open .lc-items{max-height:300px}
.lc-expand-card li{font-size:12.5px;color:var(--text2);margin-bottom:6px;padding-left:14px;position:relative;list-style:none}
.lc-expand-card li::before{content:'';position:absolute;left:0;top:6px;width:5px;height:5px;border-radius:50%;background:var(--primary)}


/* DAFO */
.dafo-grid{display:grid;grid-template-columns:1fr 1fr;gap:16px;margin-bottom:50px}
.dafo-card{background:var(--card);backdrop-filter:blur(14px);border-radius:var(--radius);padding:28px;border:1px solid rgba(255,255,255,.7);box-shadow:var(--shadow)}
.dafo-card h4{font-size:10px;font-weight:600;letter-spacing:2px;text-transform:uppercase;margin-bottom:12px;display:flex;align-items:center;gap:8px}
.dafo-card h4 .dot{width:6px;height:6px;border-radius:50%}
.dafo-card.strengths h4{color:#2ecc71}.dafo-card.strengths h4 .dot{background:#2ecc71}
.dafo-card.weaknesses h4{color:#e74c3c}.dafo-card.weaknesses h4 .dot{background:#e74c3c}
.dafo-card.opportunities h4{color:#2ecc71}.dafo-card.opportunities h4 .dot{background:#2ecc71}
.dafo-card.threats h4{color:#f39c12}.dafo-card.threats h4 .dot{background:#f39c12}
.dafo-card li{font-size:13px;color:var(--text2);margin-bottom:7px;padding-left:14px;position:relative;list-style:none}
.dafo-card li::before{content:'';position:absolute;left:0;top:7px;width:4px;height:4px;border-radius:50%;background:currentColor}

/* CAME */
.came-matrix{margin-bottom:50px}
.came-matrix-wrap{background:var(--card);backdrop-filter:blur(14px);border-radius:var(--radius);padding:32px;border:1px solid rgba(255,255,255,.7);box-shadow:var(--shadow)}
.came-matrix-header{display:grid;grid-template-columns:60px 1fr 1fr;gap:0;margin-bottom:10px}
.came-matrix-header .corner{font-size:10px;font-weight:600;color:var(--text3)}
.came-matrix-header .left,.came-matrix-header .right{text-align:center;font-size:11px;font-weight:600;letter-spacing:1px;text-transform:uppercase;color:var(--text3)}
.came-matrix-body{display:grid;grid-template-columns:40px 1fr 1fr;gap:12px}
.came-matrix-body .side-label{writing-mode:vertical-lr;transform:rotate(180deg);font-size:11px;font-weight:600;letter-spacing:2px;text-transform:uppercase;color:var(--text3);display:flex;align-items:center;justify-content:center}
.came-quadrant{border-radius:20px;padding:28px 24px;border:2px solid;transition:.3s}
.came-quadrant:hover{transform:translateY(-2px);box-shadow:var(--shadow)}
.came-quadrant.came-m{background:#f0fdf4;border-color:#a7f3d0}
.came-quadrant.came-e{background:#fffbeb;border-color:#fcd34d}
.came-quadrant.came-c{background:#fef2f2;border-color:#fecaca}
.came-quadrant.came-a{background:#f5f3ff;border-color:#c4b5fd}
.came-quadrant h4{font-family:'Lora',serif;font-size:16px;color:var(--text);margin-bottom:6px}
.came-quadrant p{font-size:12.5px;color:var(--text2);line-height:1.7;margin-bottom:6px}
.came-quadrant .came-quote{font-style:italic;color:var(--primary);font-size:13px;margin-top:8px;padding:8px 12px;background:rgba(92,184,155,.08);border-radius:8px}
@media(max-width:1024px){
  .personas-grid,.lc-expand{grid-template-columns:1fr 1fr}
}
@media(max-width:768px){
  .personas-grid,.lc-expand{grid-template-columns:1fr}
  .came-matrix-header{display:none}
  .came-matrix-body{grid-template-columns:1fr}
  .came-matrix-body .side-label{writing-mode:horizontal-tb;transform:none}

/* Table */
.data-table{width:100%;background:var(--card);backdrop-filter:blur(14px);border-radius:var(--radius);overflow:hidden;border:1px solid rgba(255,255,255,.7);box-shadow:var(--shadow);margin-bottom:40px}
.data-table table{width:100%;border-collapse:collapse}
.data-table th{padding:14px 20px;text-align:left;font-size:10px;font-weight:600;letter-spacing:2px;text-transform:uppercase;color:var(--primary);background:rgba(92,184,155,.04);border-bottom:1px solid rgba(92,184,155,.1)}
.data-table td{padding:14px 20px;font-size:13.5px;color:var(--text);border-bottom:1px solid rgba(92,184,155,.06)}
.data-table tr:hover td{background:rgba(92,184,155,.04)}
.data-table .num{text-align:right;font-family:'Inter',sans-serif;font-weight:500}

/* Price Cards */
.price-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:20px;margin-bottom:50px}
.price-card{background:var(--card);backdrop-filter:blur(14px);border-radius:var(--radius);padding:30px;border:1px solid rgba(255,255,255,.7);box-shadow:var(--shadow);transition:.3s}
.price-card:hover{transform:translateY(-3px);box-shadow:var(--shadow-lg)}
.price-card .lb{font-size:10px;font-weight:600;letter-spacing:2px;text-transform:uppercase;color:var(--primary);margin-bottom:6px}
.price-card h4{font-family:'Lora',serif;font-size:18px;color:var(--text);margin-bottom:4px}
.price-card .big{font-family:'Lora',serif;font-size:32px;color:var(--primary);margin-bottom:8px}
.price-card p{font-size:13px;color:var(--text2);line-height:1.6}

/* Distribution */
.dist-grid{display:grid;grid-template-columns:1fr 1fr;gap:20px;margin-bottom:50px}
.dist-card{background:var(--card);backdrop-filter:blur(14px);border-radius:var(--radius);padding:30px;border:1px solid rgba(255,255,255,.7);box-shadow:var(--shadow);transition:.3s}
.dist-card:hover{transform:translateY(-3px);box-shadow:var(--shadow-lg)}
.dist-card .lb{font-size:10px;font-weight:600;letter-spacing:2px;text-transform:uppercase;color:var(--primary);margin-bottom:6px}
.dist-card h4{font-family:'Lora',serif;font-size:18px;color:var(--text);margin-bottom:12px}
.dist-card li{font-size:13px;color:var(--text2);margin-bottom:6px;padding-left:14px;position:relative;list-style:none}
.dist-card li::before{content:'·';position:absolute;left:0;color:var(--primary)}

/* Promo Cards */
.promo-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:16px;margin-bottom:50px}
.promo-card{background:var(--card);backdrop-filter:blur(14px);border-radius:var(--radius);padding:26px;border:1px solid rgba(255,255,255,.7);box-shadow:var(--shadow);transition:.3s}
.promo-card:hover{transform:translateY(-3px);box-shadow:var(--shadow-lg)}
.promo-card h4{font-family:'Lora',serif;font-size:15px;color:var(--text);margin-bottom:6px}
.promo-card p{font-size:12.5px;color:var(--text2);line-height:1.6}

/* Digital Strategy */
.dig-header{display:grid;grid-template-columns:1fr 1fr 1fr;gap:20px;margin-bottom:30px}
.dig-stat{background:var(--card);backdrop-filter:blur(14px);border-radius:var(--radius);padding:28px;border:1px solid rgba(255,255,255,.7);box-shadow:var(--shadow);text-align:center}
.dig-stat .lb{font-size:10px;font-weight:600;letter-spacing:2px;text-transform:uppercase;color:var(--primary);margin-bottom:6px}
.dig-stat .val{font-family:'Lora',serif;font-size:30px;color:var(--text)}
.dig-phases{display:grid;grid-template-columns:1fr 1fr;gap:20px;margin-bottom:30px}
.dig-phase{background:var(--card);backdrop-filter:blur(14px);border-radius:var(--radius);padding:30px;border:1px solid rgba(255,255,255,.7);box-shadow:var(--shadow)}
.dig-phase .phase{font-size:10px;font-weight:600;letter-spacing:2px;text-transform:uppercase;color:var(--primary);margin-bottom:4px}
.dig-phase .budget{float:right;font-size:12px;color:var(--text3);font-weight:500}
.dig-phase h3{font-family:'Lora',serif;font-size:22px;color:var(--text);margin-bottom:16px}
.dig-metrics{display:grid;grid-template-columns:repeat(3,1fr);gap:10px;margin-bottom:16px}
.dig-metric{background:rgba(255,255,255,.5);border-radius:var(--radius-sm);padding:14px;text-align:center}
.dig-metric .lb{font-size:9px;font-weight:600;letter-spacing:1px;text-transform:uppercase;color:var(--text3);margin-bottom:4px}
.dig-metric .val{font-size:15px;font-weight:600;color:var(--text)}
.dig-kpis{display:flex;flex-wrap:wrap;gap:8px;margin-bottom:16px}
.dig-kpi{font-size:11px;padding:5px 12px;background:rgba(92,184,155,.1);border-radius:50px;color:var(--primary-dark);font-weight:500}
.btn-detail{display:inline-flex;align-items:center;gap:6px;padding:10px 20px;background:var(--primary);color:#fff;border-radius:50px;font-size:12px;font-weight:500;cursor:pointer;border:none;transition:.3s;font-family:'Inter',sans-serif}
.btn-detail:hover{transform:translateY(-2px);box-shadow:0 6px 20px rgba(92,184,155,.3)}

/* Funnel General */
.funnel-bar{margin-bottom:12px;display:flex;align-items:center;gap:14px}
.funnel-bar .name{font-size:12px;color:var(--text2);width:100px;text-align:right}
.funnel-bar .bar{flex:1;height:28px;background:linear-gradient(90deg,var(--primary),var(--primary-light));border-radius:14px;display:flex;align-items:center;padding:0 14px;font-size:12px;color:var(--primary-dark);font-weight:600;transition:.6s}

/* Modal */
.modal-overlay{position:fixed;top:0;left:0;right:0;bottom:0;background:rgba(0,0,0,.3);backdrop-filter:blur(8px);z-index:2000;display:none;align-items:center;justify-content:center;padding:20px}
.modal-overlay.show{display:flex}
.modal{background:rgba(255,255,255,.95);backdrop-filter:blur(20px);border-radius:var(--radius-lg);max-width:900px;width:100%;max-height:85vh;overflow-y:auto;padding:40px;position:relative;box-shadow:0 20px 60px rgba(0,0,0,.15)}
.modal-close{position:absolute;top:16px;right:20px;width:32px;height:32px;border:none;background:none;font-size:20px;color:var(--text3);cursor:pointer;border-radius:50%;transition:.3s;display:flex;align-items:center;justify-content:center}
.modal-close:hover{background:rgba(0,0,0,.06);color:var(--text)}
.modal h2{font-family:'Lora',serif;font-size:26px;color:var(--text);margin-bottom:6px}
.modal .sub{font-size:13px;color:var(--text2);margin-bottom:24px;line-height:1.6}
.modal-section{margin-bottom:24px}
.modal-section h3{font-size:10px;font-weight:600;letter-spacing:2px;text-transform:uppercase;color:var(--primary);margin-bottom:12px}
.modal-bar{background:rgba(255,255,255,.6);border-radius:var(--radius-sm);padding:16px 20px;margin-bottom:10px;border:1px solid rgba(255,255,255,.5)}
.modal-bar .top{display:flex;justify-content:space-between;align-items:center;margin-bottom:6px}
.modal-bar .name{font-size:13px;color:var(--text);font-weight:500}
.modal-bar .sub{font-size:11px;color:var(--text3);margin-bottom:6px}
.modal-bar .amount{font-size:14px;font-weight:600;color:var(--text)}
.modal-bar .track{height:5px;background:rgba(92,184,155,.15);border-radius:3px;overflow:hidden}
.modal-bar .fill{height:100%;background:var(--primary);border-radius:3px}
.modal-tactics{display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:20px}
.modal-tactic{background:rgba(255,255,255,.5);border-radius:var(--radius-sm);padding:16px;border:1px solid rgba(255,255,255,.5)}
.modal-tactic .num{font-size:10px;font-weight:600;color:var(--primary);margin-bottom:4px}
.modal-tactic p{font-size:12.5px;color:var(--text2);line-height:1.6}
.modal-funnel{background:rgba(255,255,255,.5);border-radius:var(--radius-sm);padding:18px;margin-bottom:10px;border:1px solid rgba(255,255,255,.5)}
.modal-funnel h4{font-size:12px;font-weight:600;color:var(--text);margin-bottom:10px}
.modal-funnel-row{display:flex;gap:6px;flex-wrap:wrap}
.modal-funnel-item{flex:1;min-width:80px;background:rgba(92,184,155,.08);border-radius:10px;padding:10px;text-align:center}
.modal-funnel-item .lb{font-size:9px;font-weight:600;letter-spacing:1px;text-transform:uppercase;color:var(--primary);margin-bottom:2px}
.modal-funnel-item .val{font-size:13px;font-weight:600;color:var(--text)}
.modal-kpis{display:grid;grid-template-columns:repeat(3,1fr);gap:10px}
.modal-kpi{background:rgba(255,255,255,.5);border-radius:var(--radius-sm);padding:16px;text-align:center}
.modal-kpi .lb{font-size:9px;font-weight:600;letter-spacing:1px;text-transform:uppercase;color:var(--primary);margin-bottom:4px}
.modal-kpi .val{font-size:16px;font-weight:600;color:var(--text)}

/* Financial */
.fin-stats{display:grid;grid-template-columns:repeat(4,1fr);gap:16px;margin-bottom:40px}
.fin-stat{background:var(--card);backdrop-filter:blur(14px);border-radius:var(--radius);padding:24px;border:1px solid rgba(255,255,255,.7);box-shadow:var(--shadow)}
.fin-stat .lb{font-size:10px;font-weight:600;letter-spacing:2px;text-transform:uppercase;color:var(--primary);margin-bottom:6px}
.fin-stat .val{font-family:'Lora',serif;font-size:22px;color:var(--text)}

/* Simulator */
.sim-grid{display:grid;grid-template-columns:1fr 1fr;gap:24px;margin-bottom:50px}
.sim-controls{background:var(--card);backdrop-filter:blur(14px);border-radius:var(--radius);padding:30px;border:1px solid rgba(255,255,255,.7);box-shadow:var(--shadow)}
.sim-controls h3{font-size:10px;font-weight:600;letter-spacing:2px;text-transform:uppercase;color:var(--primary);margin-bottom:6px}
.sim-controls .sub{font-size:12px;color:var(--text2);margin-bottom:20px;line-height:1.5}
.sim-row{margin-bottom:20px}
.sim-row .top{display:flex;justify-content:space-between;align-items:center;margin-bottom:8px}
.sim-row .name{font-size:13px;color:var(--text);font-weight:500}
.sim-row .val{font-size:13px;color:var(--text);font-weight:600}
.sim-row .real{font-size:11px;color:var(--text3)}
.sim-slider{width:100%;height:6px;-webkit-appearance:none;appearance:none;background:linear-gradient(90deg,var(--primary) 0%,var(--primary) var(--progress,50%),rgba(92,184,155,.15) var(--progress,50%),rgba(92,184,155,.15) 100%);border-radius:3px;outline:none;cursor:pointer}
.sim-slider::-webkit-slider-thumb{-webkit-appearance:none;width:18px;height:18px;border-radius:50%;background:var(--primary);cursor:pointer;box-shadow:0 2px 8px rgba(92,184,155,.3)}
.sim-slider-wrap{position:relative;padding-top:8px}
.sim-real-marker{position:absolute;left:var(--real);top:11px;width:12px;height:12px;border-radius:50%;background:#ec4899;border:2px solid #fff;box-shadow:0 2px 10px rgba(236,72,153,.35);transform:translateX(-50%);z-index:3;pointer-events:none}
.sim-real-marker::after{content:'Allora real';position:absolute;left:50%;top:15px;transform:translateX(-50%);font-size:9px;font-weight:600;white-space:nowrap;color:#ec4899}
.sim-results{display:grid;grid-template-columns:1fr 1fr;gap:14px}
.sim-result{background:var(--card);backdrop-filter:blur(14px);border-radius:var(--radius);padding:22px;border:1px solid rgba(255,255,255,.7);box-shadow:var(--shadow)}
.sim-result .lb{font-size:10px;font-weight:600;letter-spacing:2px;text-transform:uppercase;color:var(--primary);margin-bottom:6px}
.sim-result .val{font-family:'Lora',serif;font-size:24px;color:var(--text)}
.btn-reset{display:inline-flex;align-items:center;gap:6px;padding:8px 18px;background:none;border:1px solid rgba(92,184,155,.3);border-radius:50px;font-size:12px;color:var(--primary);cursor:pointer;transition:.3s;font-family:'Inter',sans-serif;margin-bottom:16px}
.btn-reset:hover{background:var(--primary);color:#fff}
.sim-summary{display:grid;grid-template-columns:repeat(3,1fr);gap:10px;margin-top:16px}
.sim-sum-item{background:rgba(255,255,255,.5);border-radius:10px;padding:12px;text-align:center}
.sim-sum-item .lb{font-size:9px;font-weight:600;letter-spacing:1px;text-transform:uppercase;color:var(--text3);margin-bottom:2px}
.sim-sum-item .val{font-size:13px;font-weight:600;color:var(--text)}

/* Break Even Chart */
.chart-container{background:var(--card);backdrop-filter:blur(14px);border-radius:var(--radius);padding:30px;border:1px solid rgba(255,255,255,.7);box-shadow:var(--shadow);margin-bottom:50px;position:relative;height:380px}
.chart-svg{width:100%;height:100%}

/* Projections */
.proj-grid{display:grid;grid-template-columns:1fr 1fr;gap:24px;margin-bottom:50px}
.proj-chart{background:var(--card);backdrop-filter:blur(14px);border-radius:var(--radius);padding:30px;border:1px solid rgba(255,255,255,.7);box-shadow:var(--shadow);position:relative;height:300px}
.proj-cards{display:flex;flex-direction:column;gap:14px}
.proj-card{background:var(--card);backdrop-filter:blur(14px);border-radius:var(--radius);padding:24px;border:1px solid rgba(255,255,255,.7);box-shadow:var(--shadow);display:flex;align-items:center;gap:16px}
.proj-card .year{font-family:'Lora',serif;font-size:28px;color:var(--text);min-width:60px}
.proj-card .info{flex:1}
.proj-card .info .row{display:flex;justify-content:space-between;font-size:12.5px;color:var(--text2);margin-bottom:2px}
.proj-card .info .row span:last-child{font-weight:600;color:var(--text)}
.proj-card .bar-wrap{width:100px;height:6px;background:rgba(92,184,155,.15);border-radius:3px;overflow:hidden}
.proj-card .bar-fill{height:100%;background:var(--primary);border-radius:3px}

/* Bar Chart */
.bar-chart{background:var(--card);backdrop-filter:blur(14px);border-radius:var(--radius);padding:30px;border:1px solid rgba(255,255,255,.7);box-shadow:var(--shadow);margin-bottom:40px}
.bar-chart h3{font-family:'Lora',serif;font-size:18px;color:var(--text);margin-bottom:20px}
.bar-row{display:flex;align-items:center;gap:14px;margin-bottom:10px}
.bar-row .name{width:120px;font-size:12px;color:var(--text2);text-align:right}
.bar-row .bar{flex:1;height:24px;background:rgba(92,184,155,.15);border-radius:12px;overflow:hidden}
.bar-row .fill{height:100%;background:linear-gradient(90deg,var(--primary),var(--primary-light));border-radius:12px;display:flex;align-items:center;padding:0 10px;font-size:11px;color:var(--primary-dark);font-weight:600;transition:.6s}

/* P&L Chart */
.pl-chart{background:var(--card);backdrop-filter:blur(14px);border-radius:var(--radius);padding:30px;border:1px solid rgba(255,255,255,.7);box-shadow:var(--shadow);margin-bottom:40px;position:relative;height:350px}

/* Connected Chapters */
.connected{display:grid;grid-template-columns:1fr 1fr;gap:16px;margin-top:50px}
.connected-link{background:var(--card);backdrop-filter:blur(14px);border-radius:var(--radius);padding:24px 28px;border:1px solid rgba(255,255,255,.7);box-shadow:var(--shadow);display:flex;align-items:center;justify-content:space-between;text-decoration:none;color:var(--text);transition:.3s}
.connected-link:hover{transform:translateY(-3px);box-shadow:var(--shadow-lg)}
.connected-link .lb{font-size:10px;font-weight:600;letter-spacing:2px;text-transform:uppercase;color:var(--primary);margin-bottom:4px}
.connected-link .title{font-family:'Lora',serif;font-size:17px}
.connected-link .arr{color:var(--primary);font-size:18px}

/* Constellation Map Modal */
.constellation{position:relative;width:400px;height:400px;margin:0 auto}
.constellation svg{width:100%;height:100%}
.const-dot{position:absolute;width:56px;height:56px;border-radius:50%;background:var(--card);backdrop-filter:blur(10px);border:2px solid rgba(255,255,255,.8);box-shadow:0 4px 20px rgba(0,0,0,.08);display:flex;flex-direction:column;align-items:center;justify-content:center;cursor:pointer;transition:.3s;text-decoration:none;color:var(--text)}
.const-dot:hover{transform:scale(1.1);box-shadow:0 8px 30px rgba(0,0,0,.12)}
.const-dot .letter{font-family:'Lora',serif;font-size:18px;font-weight:600}
.const-dot .name{font-size:9px;color:var(--text3);margin-top:1px}

/* Animations */
@keyframes fadeUp{from{opacity:0;transform:translateY(24px)}to{opacity:1;transform:translateY(0)}}
.anim{animation:fadeUp .7s cubic-bezier(.4,0,.2,1) forwards;opacity:0}
.d1{animation-delay:.1s}.d2{animation-delay:.2s}.d3{animation-delay:.3s}.d4{animation-delay:.4s}.d5{animation-delay:.5s}.d6{animation-delay:.6s}

/* Responsive */
@media(max-width:1024px){
.cards-3,.tam-grid,.pestel-grid,.trends-grid,.chain-grid,.life-grid,.came-grid,.price-grid,.promo-grid{grid-template-columns:1fr 1fr}
.bmc-grid{grid-template-columns:repeat(3,1fr)}
.comp-grid,.dist-grid,.dig-phases,.proj-grid,.sim-grid,.dafo-grid{grid-template-columns:1fr}
.fin-stats{grid-template-columns:1fr 1fr}
}
@media(max-width:768px){
.cards-3,.tam-grid,.pestel-grid,.trends-grid,.chain-grid,.life-grid,.came-grid,.price-grid,.promo-grid,.fin-stats{grid-template-columns:1fr}
.bmc-grid{grid-template-columns:1fr 1fr}
.nav-items{display:none}
.section{padding:80px 20px 40px}
}

/* Monthly detail table */
.monthly-table{width:100%;border-collapse:collapse;margin-top:16px}
.monthly-table th{padding:8px 10px;text-align:right;font-size:10px;font-weight:600;letter-spacing:1px;text-transform:uppercase;color:var(--primary);border-bottom:1px solid rgba(92,184,155,.1)}
.monthly-table th:first-child{text-align:left}
.monthly-table td{padding:8px 10px;text-align:right;font-size:12px;color:var(--text);border-bottom:1px solid rgba(92,184,155,.06)}
.monthly-table td:first-child{text-align:left;font-weight:500;color:var(--text2)}
.monthly-table .neg{color:#e74c3c}
.monthly-table .pos{color:#2ecc71}
.monthly-table tr:last-child td{font-weight:600;border-top:2px solid rgba(92,184,155,.15)}
</style>
</head>
<body>
<div class="bg-orbs"><div class="orb orb-1"></div><div class="orb orb-2"></div><div class="orb orb-3"></div></div>
<div class="dd-overlay" id="ddOverlay"></div>
<div class="content">

<!-- NAV -->
<nav class="nav-wrap">
<div class="nav-bar">
<a href="#inicio" class="nav-logo">
<svg viewBox="0 0 24 24" fill="none"><path d="M12 2L13.09 8.26L18 4L14.74 9.91L21 12L14.74 14.09L18 20L13.09 15.74L12 22L10.91 15.74L6 20L9.26 14.09L3 12L9.26 9.91L6 4L10.91 8.26L12 2Z" fill="#5cb89b"/></svg>
<span>Allora</span>
</a>
<ul class="nav-items" id="navItems">
<li class="nav-item"><button class="nav-btn" data-dd="dd-inicio">Inicio<svg class="arr" viewBox="0 0 10 10"><path d="M1 3.5L5 7L9 3.5" stroke="currentColor" stroke-width="1.5" fill="none" stroke-linecap="round"/></svg></button><div class="dd" id="dd-inicio"><a href="#inicio">Identidad</a><a href="#quiz">Buyer Persona</a><a href="#tam">Mercado</a></div></li>
<li class="nav-item"><button class="nav-btn" data-dd="dd-analisis">Análisis<svg class="arr" viewBox="0 0 10 10"><path d="M1 3.5L5 7L9 3.5" stroke="currentColor" stroke-width="1.5" fill="none" stroke-linecap="round"/></svg></button><div class="dd" id="dd-analisis"><a href="#pestel">PESTEL</a><a href="#porter">Porter</a><a href="#competidores">Competidores</a><a href="#tendencias">Tendencias</a><a href="#bmc">Business Model Canvas</a></div></li>
<li class="nav-item"><button class="nav-btn" data-dd="dd-estrategia">Estrategia<svg class="arr" viewBox="0 0 10 10"><path d="M1 3.5L5 7L9 3.5" stroke="currentColor" stroke-width="1.5" fill="none" stroke-linecap="round"/></svg></button><div class="dd" id="dd-estrategia"><a href="#cadena">Cadena de valor</a><a href="#posicionamiento">Posicionamiento</a><a href="#ciclo">Ciclo de vida</a><a href="#dafo">SWOT / DAFO</a><a href="#came">CAME</a></div></li>
<li class="nav-item"><button class="nav-btn" data-dd="dd-marketing">Marketing Mix<svg class="arr" viewBox="0 0 10 10"><path d="M1 3.5L5 7L9 3.5" stroke="currentColor" stroke-width="1.5" fill="none" stroke-linecap="round"/></svg></button><div class="dd" id="dd-marketing"><a href="#producto">Producto</a><a href="#precio">Precio</a><a href="#distribucion">Distribución</a><a href="#promocion">Promoción</a></div></li>
<li class="nav-item"><button class="nav-btn" data-dd="dd-digital">Digital<svg class="arr" viewBox="0 0 10 10"><path d="M1 3.5L5 7L9 3.5" stroke="currentColor" stroke-width="1.5" fill="none" stroke-linecap="round"/></svg></button><div class="dd" id="dd-digital"><a href="#resumen-digital">Resumen</a><a href="#awareness">Awareness</a><a href="#captacion">Captación</a><a href="#conversion">Conversión</a><a href="#fidelizacion">Fidelización</a><a href="#funnel-general">Funnel</a></div></li>
<li class="nav-item"><button class="nav-btn" data-dd="dd-finanzas">Finanzas<svg class="arr" viewBox="0 0 10 10"><path d="M1 3.5L5 7L9 3.5" stroke="currentColor" stroke-width="1.5" fill="none" stroke-linecap="round"/></svg></button><div class="dd" id="dd-finanzas"><a href="#simulador">Simulador</a><a href="#break-even">Punto de equilibrio</a><a href="#proyecciones">Proyecciones</a><a href="#unidades">Unidades</a><a href="#resultados">Resultados generales</a><a href="#panel">Panel de Presupuesto</a></div></li>
</ul>
<div class="nav-right">
<button class="nav-map-btn" id="mapBtn">
<svg width="16" height="16" viewBox="0 0 16 16" fill="none"><circle cx="8" cy="8" r="6" stroke="currentColor" stroke-width="1.5"/><circle cx="8" cy="8" r="2" fill="currentColor"/></svg>
Mi Mapa
</button>
<div class="nav-user"><span class="dot"></span>Sandra</div>
</div>
</div>
</nav>

<!-- HERO -->
<section class="hero" id="inicio">
<div class="hero-badge anim d1">
<svg viewBox="0 0 14 14" fill="none"><path d="M7 1L7.67 4.33L10 2.5L8.33 5.33L11.5 6.5L8.33 7.67L10 10.5L7.67 8.67L7 12L6.33 8.67L4 10.5L5.67 7.67L2.5 6.5L5.67 5.33L4 2.5L6.33 4.33L7 1Z" fill="#3a7a6a"/></svg>
JOYERÍA CON SIGNIFICADO · BOGOTÁ
</div>
<h1 class="hero-h1 anim d2">Esto no es una joya.</h1>
<h2 class="hero-h2 anim d3">Es un momento de tu historia.</h2>
<p class="hero-p anim d4">Allora es un viaje íntimo a través de tu identidad. Cada pieza es un amuleto contemporáneo que acompaña tu evolución.</p>
<a href="#quiz" class="btn-primary anim d5">Descubre qué amuleto eres <svg viewBox="0 0 18 18" fill="none"><path d="M4 9H14M14 9L10 5M14 9L10 13" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/></svg></a>
</section>

<!-- MISSION VISION VALUES -->
<section class="section">
<div class="cards-3">
<div class="glass-card anim d3">
<div class="card-label">Misión</div>
<p class="card-text">Diseñar amuletos contemporáneos que acompañen la evolución personal de cada mujer, uniendo artesanía, simbolismo y narrativa.</p>
</div>
<div class="glass-card anim d4">
<div class="card-label">Visión</div>
<p class="card-text">Ser la marca colombiana referente de joyería maximalista con significado, construyendo una comunidad global de creyentes del amuleto para 2030.</p>
</div>
<div class="glass-card anim d5">
<div class="card-label">Valores</div>
<p class="card-text">Allora nace de la idea de que cada joya es un espejo del momento interior. No vendemos objetos: entregamos símbolos que acompañan ciclos, transformaciones y compromisos íntimos.</p>
<div class="card-tags">
<span class="tag">Continuidad</span><span class="tag">Fluidez</span><span class="tag">Evolución</span><span class="tag">Autenticidad</span><span class="tag">Artesanía</span>
</div>
</div>
</div>
</section>

<!-- QUIZ -->
<section class="section" id="quiz">
<div class="quiz-wrap">
<span class="chapter-label anim">Ritual de Identidad</span>
<h2 class="section-title anim" style="text-align:center;margin-bottom:30px">¿Qué amuleto vive en ti?</h2>
<div class="quiz-card" id="quizCard">
 <div class="personas-summary anim d4">
  <h3 style="font-family:'Lora',serif;font-size:24px;color:var(--text);margin-bottom:8px;text-align:center">Nuestros Buyer Personas</h3>
  <p style="font-size:14px;color:var(--text3);text-align:center;margin-bottom:30px">Conoce los perfiles que inspiran cada colección de Allora</p>
  <div class="personas-grid">
    <div class="persona-card">
      <div class="persona-avatar" style="background:linear-gradient(135deg,#d1fae5,#a7f3d0)">🌿</div>
      <h4>Sandra Arena</h4>
      <div class="persona-sub">Compra Personal · Intención Estética</div>
      <p class="persona-desc">Diseñadora gráfica de 25 años en Bogotá. Valora el trabajo hecho a mano, el consumo consciente y las historias detrás de cada pieza.</p>
      <div class="persona-detail"><strong>Digital & Consumo</strong>Nivel de digitalización medio-alto. Descubre proyectos independientes en redes y prefiere marcas transparentes.</div>
      <div class="persona-piece">Pieza ideal: Collar Mística Ancestral</div>
    </div>
    <div class="persona-card">
      <div class="persona-avatar" style="background:linear-gradient(135deg,#dbeafe,#93c5fd)">🎁</div>
      <h4>Andrés Medulla</h4>
      <div class="persona-sub">Compra de Regalo · Valor Emocional</div>
      <p class="persona-desc">Ejecutivo comercial de 30 años. Cuando necesita hacer un regalo importante busca objetos significativos con valor emocional.</p>
      <div class="persona-detail"><strong>Digital & Consumo</strong>Digitalización muy alta. Valora rapidez, compra simple y una guía clara sobre el significado de las piezas.</div>
      <div class="persona-piece">Pieza ideal: Choker Corazón Sagrado</div>
    </div>
    <div class="persona-card">
      <div class="persona-avatar" style="background:linear-gradient(135deg,#ede9fe,#c4b5fd)">🔮</div>
      <h4>Rocío Vera</h4>
      <div class="persona-sub">Compra de Amuleto · Protección Espiritual</div>
      <p class="persona-desc">Psicóloga en formación de 29 años que atraviesa cambios personales. Busca objetos cargados de intención y protección.</p>
      <div class="persona-detail"><strong>Digital & Consumo</strong>Investiga el origen de los materiales y el simbolismo ancestral; rechaza la producción masiva sin significado.</div>
      <div class="persona-piece">Pieza ideal: Brazalete Talismán</div>
    </div>
  </div>
</div>
<!-- Quiz content injected by JS -->
</div>
</div>
</section>

<!-- TAM SAM SOM -->
<section class="section" id="tam">
<span class="chapter-label anim">Mercado</span>
<h2 class="section-title anim">TAM · SAM · SOM</h2>
<p class="section-sub anim">Toca cada esfera para revelar la dimensión real del mercado.</p>
<div class="tam-grid anim d2">
<div class="tam-card" onclick="showTam('tam')">
<div class="plus">+</div>
<div class="letter">TAM</div>
<div class="sub">Mercado total Bogotá</div>
<div class="amount">€247.000.000</div>
<div class="hint">Toca para ver el detalle</div>
</div>
<div class="tam-card" onclick="showTam('sam')">
<div class="plus">+</div>
<div class="letter">SAM</div>
<div class="sub">Mercado disponible</div>
<div class="amount">€209.000.000</div>
<div class="hint">Toca para ver el detalle</div>
</div>
<div class="tam-card" onclick="showTam('som')">
<div class="plus">+</div>
<div class="letter">SOM</div>
<div class="sub">Objetivo año 1</div>
<div class="amount">€378.957</div>
<div class="hint">Toca para ver el detalle</div>
</div>
</div>
<div class="tam-detail anim d3" id="tamDetail">
<div class="lb" id="tamDetailLb">TAM · Objetivo año 1</div>
<div class="amount" id="tamDetailAmount">€378.957</div>
<p id="tamDetailText">2.500 piezas anuales, objetivo realista para los primeros 12 meses; proyección a 6.250 piezas (€947.393) en 24 meses.</p>
</div>
</section>

<!-- Connected Chapters -->
<div class="section" style="padding-top:20px;padding-bottom:60px">
<span class="chapter-label anim" style="display:block;text-align:center;margin-bottom:16px">Sigue tu viaje</span>
<h3 class="anim" style="font-family:'Lora',serif;font-size:24px;text-align:center;margin-bottom:24px;color:var(--text)">Capítulos conectados</h3>
<div class="connected anim d2">
<a href="#pestel" class="connected-link"><div><div class="lb">Explora</div><div class="title">Análisis</div></div><span class="arr">→</span></a>
<a href="#cadena" class="connected-link"><div><div class="lb">Explora</div><div class="title">Estrategia</div></div><span class="arr">→</span></a>
</div>
</div>

<!-- PESTEL -->
<section class="section" id="pestel">
<span class="chapter-label anim">Capítulo 1</span>
<h2 class="section-title anim">Análisis del entorno</h2>
<p class="section-sub anim">Un mapa de fuerzas externas y de mercado que da forma a la oportunidad de Allora.</p>
<h3 style="font-family:'Lora',serif;font-size:24px;margin-bottom:20px" class="anim">PESTEL</h3>
<div class="pestel-grid anim d2">
<div class="pestel-item active" onclick="showPestel('p')"><div class="big">P</div><div class="lbl">Político</div></div>
<div class="pestel-item" onclick="showPestel('e')"><div class="big">E</div><div class="lbl">Económico</div></div>
<div class="pestel-item" onclick="showPestel('s')"><div class="big">S</div><div class="lbl">Social</div></div>
<div class="pestel-item" onclick="showPestel('t')"><div class="big">T</div><div class="lbl">Tecnológico</div></div>
<div class="pestel-item" onclick="showPestel('ec')"><div class="big">E</div><div class="lbl">Ecológico</div></div>
<div class="pestel-item" onclick="showPestel('l')"><div class="big">L</div><div class="lbl">Legal</div></div>
</div>
<div class="pestel-detail anim d3" id="pestelDetail">
<h3 id="pestelH3">Político</h3>
<h4 id="pestelH4">Estabilidad moderada y polarización alta.</h4>
<ul id="pestelList">
<li>Apoyo gubernamental a PYMES y emprendimiento creativo.</li>
<li>Incertidumbre por posibles decretos fiscales.</li>
<li>Seguridad territorial afecta cadenas de suministro locales.</li>
</ul>
</div>
</section>

<!-- PORTER -->
<section class="section" id="porter">
<h3 style="font-family:'Lora',serif;font-size:24px;margin-bottom:24px" class="anim">Cinco fuerzas de Porter</h3>
<div class="anim d2">
<div class="porter-bar">
<div class="top"><span class="name">Nuevos entrantes</span><span class="level">Alto</span></div>
<div class="track"><div class="fill" style="width:75%"></div></div>
<p class="desc">Costo de metales, escasez de talento especializado y competencia asiática elevan barreras.</p>
</div>
<div class="porter-bar">
<div class="top"><span class="name">Poder de proveedores</span><span class="level">Medio-Alto</span></div>
<div class="track"><div class="fill" style="width:60%"></div></div>
<p class="desc">Alto cuando hay metales diferenciados; Allora diversifica y usa proveedores locales.</p>
</div>
<div class="porter-bar">
<div class="top"><span class="name">Poder de compradores</span><span class="level">Alto</span></div>
<div class="track"><div class="fill" style="width:78%"></div></div>
<p class="desc">Acceso digital a información y variedad. Se mitiga con diferenciación simbólica.</p>
</div>
<div class="porter-bar">
<div class="top"><span class="name">Productos sustitutos</span><span class="level">Medio-Alto</span></div>
<div class="track"><div class="fill" style="width:55%"></div></div>
<p class="desc">Pañuelos, broches, DIY y segunda mano satisfacen autoexpresión.</p>
</div>
<div class="porter-bar">
<div class="top"><span class="name">Rivalidad interna</span><span class="level">Medio-Alto</span></div>
<div class="track"><div class="fill" style="width:62%"></div></div>
<p class="desc">Baja inversión inicial facilita entrada; reto = fidelizar y diferenciar.</p>
</div>
</div>
</section>

<!-- COMPETIDORES -->
<section class="section" id="competidores">
<h3 style="font-family:'Lora',serif;font-size:24px;margin-bottom:24px" class="anim">Competidores</h3>
<div class="comp-grid anim d2">
<div class="comp-card">
<div class="comp-browser"><div class="dots"><span></span><span></span><span></span></div><span class="url">pajarapinta.co</span></div>
<div class="comp-img-placeholder" style="background:linear-gradient(135deg,#d4a574,#8b6f47)"></div>
<div class="comp-info">
<a href="#" class="comp-link" onclick="event.preventDefault()">Visitar ↗</a>
<h3>Pájara Pinta</h3>
<div class="price">€30 – €75</div>
<div class="desc">Estética orgánica y artesanal</div>
<span class="tag">Accesible</span>
</div>
</div>
<div class="comp-card">
<div class="comp-browser"><div class="dots"><span></span><span></span><span></span></div><span class="url">danielasalcedo.com</span></div>
<div class="comp-img-placeholder" style="background:linear-gradient(135deg,#f0c4d4,#d4a0b0)"></div>
<div class="comp-info">
<a href="#" class="comp-link" onclick="event.preventDefault()">Visitar ↗</a>
<h3>Daniela Salcedo</h3>
<div class="price">€110 – €220</div>
<div class="desc">Diseño vanguardista y status</div>
<span class="tag">Premium</span>
</div>
</div>
<div class="comp-card">
<div class="comp-browser"><div class="dots"><span></span><span></span><span></span></div><span class="url">international.filamental.shop</span></div>
<div class="comp-img-placeholder" style="background:linear-gradient(135deg,#c4e8c4,#7cb07c)"></div>
<div class="comp-info">
<a href="#" class="comp-link" onclick="event.preventDefault()">Visitar ↗</a>
<h3>Filamental</h3>
<div class="price">€145 – €290</div>
<div class="desc">Piezas de gala, gran formato</div>
<span class="tag">Alto lujo</span>
</div>
</div>
<div class="comp-card">
<div class="comp-browser"><div class="dots"><span></span><span></span><span></span></div><span class="url">allora.shop</span></div>
<div class="comp-img-placeholder" style="background:linear-gradient(135deg,#e8f5f0,#f0e8f5)">✨</div>
<div class="comp-info">
<h3>Allora</h3>
<div class="price">€26 – €180</div>
<div class="desc">Amuletos con narrativa evolutiva</div>
<span class="tag" style="background:var(--primary);color:#fff">Allora</span>
</div>
</div>
</div>
</section>

<!-- TENDENCIAS -->
<section class="section" id="tendencias">
<h3 style="font-family:'Lora',serif;font-size:24px;margin-bottom:24px" class="anim">Tendencias del mercado</h3>
<div class="trends-grid anim d2">
<div class="trend-card"><h4>Maximalismo 2026</h4><p>Piezas grandes, superposición, color.</p></div>
<div class="trend-card"><h4>Joyería simbólica</h4><p>Amuletos, runas, elementos ancestrales.</p></div>
<div class="trend-card"><h4>Consumo consciente</h4><p>Trazabilidad, materiales éticos.</p></div>
<div class="trend-card"><h4>Social commerce</h4><p>TikTok Shop, Instagram Shopping.</p></div>
</div>
</section>

<!-- BMC -->
<section class="section" id="bmc">
<h3 style="font-family:'Lora',serif;font-size:24px;margin-bottom:8px" class="anim">Business Model Canvas</h3>
<p class="section-sub anim" style="margin-bottom:24px">Pasa el cursor sobre cualquier bloque del lienzo para ver el detalle. En móvil, toca el bloque.</p>
<div class="bmc-grid anim d2">
<div class="bmc-cell" onclick="toggleBmc(this)"><div class="icon">🤝</div><div class="eng">Key Partners</div><div class="sp">Alianzas estratégicas</div><div class="details">• Serie de entrevistas con videntes en el blog, trasladables a un canal de Spotify.<br>• Consultorio digital con una vidente: "El oráculo Allora".</div></div>
<div class="bmc-cell" onclick="toggleBmc(this)"><div class="icon">⚡</div><div class="eng">Key Activities</div><div class="sp">Actividades clave</div><div class="details">• Community management<br>• Gestión de campañas<br>• Gestión de contenidos<br>• Gestión de web y SEO<br>• Gestión e-commerce<br>• Email automatizado</div></div>
<div class="bmc-cell" onclick="toggleBmc(this)"><div class="icon">✨</div><div class="eng">Value Propositions</div><div class="sp">Propuesta de estrategia digital</div><div class="details">• Joyas como amuletos y conexión emocional.<br>• Diferenciación narrativa (storytelling).<br>• Lujo artesanal maximalista hecho a mano.<br>• Acompañamiento en la narrativa personal.</div></div>
<div class="bmc-cell" onclick="toggleBmc(this)"><div class="icon">♡</div><div class="eng">Customer Relationships</div><div class="sp">Canales de atención y relación</div><div class="details"><b>SOPORTE</b><br>• Vía web, formulario, centro de ayuda y guía de cuidado de joyería.<br><b>FIDELIZACIÓN</b><br>• A través de email.<br><b>COMUNIDAD SOCIAL</b><br>• Chat de comunidad en Instagram y TikTok: UGC-micro-influencers.</div></div>
<div class="bmc-cell" onclick="toggleBmc(this)"><div class="icon">👥</div><div class="eng">Customer Segments</div><div class="sp">Usuarios y clientes online</div><div class="details">• B2C<br>• Mujeres de 20-35 años<br>• Activas en redes sociales (TikTok, Instagram)<br>• Sensibles al consumo simbólico</div></div>
<div class="bmc-cell" onclick="toggleBmc(this)"><div class="icon">📦</div><div class="eng">Key Resources</div><div class="sp">Recursos necesarios</div><div class="details">• Talento digital y creativo<br>• Expertos en e-commerce<br>• Presupuesto de publicidad pagada<br>• Plataforma de e-commerce<br>• Herramientas de CRM<br>• Plataformas de marketing automation<br>• Herramientas de analítica</div></div>
<div class="bmc-cell" onclick="toggleBmc(this)"><div class="icon">🔗</div><div class="eng">Channels</div><div class="sp">Canales de contacto</div><div class="details"><b>CAPTACIÓN DE USUARIOS</b><br>• Campañas Meta Ads / TikTok Ads<br>• Email de captación con descuento<br>• Campañas de SEM<br><b>PLATAFORMAS DE CONVERSIÓN</b><br>• Venta en web oficial D2C<br>• Campañas de retargeting<br>• Email de conversión</div></div>
<div class="bmc-cell wide" onclick="toggleBmc(this)"><div class="icon">💰</div><div class="eng">Cost Structure</div><div class="sp">Estructura de costes</div><div class="details"><b>FIJOS</b><br>• Plataforma e-commerce • CRM y email marketing • Automatización • Analítica y tracking • Pasarelas de pago • Mantenimiento web y UX/UI • Base de datos • Licencias operativas • Producción de contenido • Gestión RRSS<br><b>VARIABLES</b><br>• Paid media • PR digital • Influencer advocacy • Seeding • Fees de agencias • Creación de contenido</div></div>
<div class="bmc-cell wide" onclick="toggleBmc(this)"><div class="icon">📈</div><div class="eng">Revenue Streams</div><div class="sp">Resultados</div><div class="details">• Inbound leads: campañas SEM, TikTok Ads, IG Ads y email marketing.<br>• Referral leads: clientes actuales y marketing de afiliación.<br>• Ventas por canal: sitio web (D2C).<br>• Alcance y engagement: RRSS + influencer marketing + UGC.<br>• Optimizaciones de marketing.</div></div>
</div>
</section>

<!-- Connected Chapters -->
<div class="section" style="padding-top:20px;padding-bottom:60px">
<span class="chapter-label anim" style="display:block;text-align:center;margin-bottom:16px">Sigue tu viaje</span>
<h3 class="anim" style="font-family:'Lora',serif;font-size:24px;text-align:center;margin-bottom:24px;color:var(--text)">Capítulos conectados</h3>
<div class="connected anim d2">
<a href="#cadena" class="connected-link"><div><div class="lb">Explora</div><div class="title">Estrategia</div></div><span class="arr">→</span></a>
<a href="#producto" class="connected-link"><div><div class="lb">Explora</div><div class="title">Marketing Mix</div></div><span class="arr">→</span></a>
</div>
</div>

<!-- CADENA DE VALOR -->
<section class="section" id="cadena">
<span class="chapter-label anim">Capítulo 2</span>
<h2 class="section-title anim">Estrategia competitiva</h2>
<p class="section-sub anim">Cómo Allora se posiciona, evoluciona y se diferencia en el ecosistema joyero colombiano.</p>
<h3 style="font-family:'Lora',serif;font-size:24px;margin-bottom:20px" class="anim">Cadena de valor</h3>
<div class="value-chain-container anim d2">
  <div class="vc-wrapper">
    <div class="vc-grid">
      <div class="vc-support-label">Actividades de apoyo</div>
      <div class="vc-support">
        <div class="vc-support-item si"><div class="vc-icon" style="background:#ede9fe">🏢</div><div class="vc-text"><h4>Infraestructura de la empresa</h4><p>Gestión · Finanzas · Tecnología</p></div></div>
        <div class="vc-support-item rrhh"><div class="vc-icon" style="background:#d1fae5">👥</div><div class="vc-text"><h4>Gestión de RRHH</h4><p>Contratación · Capacitación · Cultura organizacional</p></div></div>
        <div class="vc-support-item tech"><div class="vc-icon" style="background:#dbeafe">💻</div><div class="vc-text"><h4>Desarrollo tecnológico</h4><p>Diseño · Innovación · Plataformas digitales</p></div></div>
        <div class="vc-support-item aprov"><div class="vc-icon" style="background:#fef3c7">📦</div><div class="vc-text"><h4>Aprovisionamiento</h4><p>Proveedores · Materias primas · Logística</p></div></div>
      </div>
      <div style="grid-column:3;grid-row:1/span 4;display:flex;align-items:center;justify-content:center"><div class="vc-margin">Margen</div></div>
    </div>
    <div style="border-top:2px dashed rgba(92,184,155,.2);margin:16px 0"></div>
    <div class="vc-primary-label">Actividades primarias</div>
    <div style="display:grid;grid-template-columns:auto 1fr;gap:0;margin-top:16px">
      <div class="vc-support-label">Primarias</div>
      <div style="display:grid;grid-template-columns:repeat(9,1fr);gap:8px;min-width:760px">
        <div class="vc-primary-item li"><h4>Logística interna</h4><ul><li>Recepción materias primas</li><li>Almacenamiento</li></ul></div>
        <div class="vc-arrow">→</div>
        <div class="vc-primary-item op"><h4>Operaciones</h4><ul><li>Diseño</li><li>Producción artesanal</li><li>Control calidad</li></ul></div>
        <div class="vc-arrow">→</div>
        <div class="vc-primary-item le"><h4>Logística externa</h4><ul><li>Distribución</li><li>E-commerce</li></ul></div>
        <div class="vc-arrow">→</div>
        <div class="vc-primary-item mk"><h4>Marketing y ventas</h4><ul><li>Comunicación digital</li><li>Redes sociales</li><li>Ventas online</li></ul></div>
        <div class="vc-arrow">→</div>
        <div class="vc-primary-item ps"><h4>Servicio postventa</h4><ul><li>Atención cliente</li><li>Fidelización</li><li>Reparación</li></ul></div>
      </div>
    </div>
  </div>
</div>
</section>

<!-- POSICIONAMIENTO -->
<section class="section" id="posicionamiento">
<h3 style="font-family:'Lora',serif;font-size:24px;margin-bottom:8px" class="anim">Posicionamiento</h3>
<p class="section-sub anim">Mapa de posicionamiento por precio y exclusividad percibida.</p>
<div class="pos-map anim d2">
<div class="lbl-y1">EXCLUSIVIDAD +</div>
<div class="lbl-y2">EXCLUSIVIDAD –</div>
<div class="lbl-x1">PRECIO –</div>
<div class="lbl-x2">PRECIO +</div>
<div class="axis-x"></div>
<div class="axis-y"></div>
<div class="pos-dot" style="bottom:18%;left:20%"><div class="label">Pájara Pinta<span class="price">$120K - 300K</span></div></div>
<div class="pos-dot" style="bottom:74%;left:58%"><div class="label" style="background:var(--primary);color:#fff">Allora<span class="price" style="color:rgba(255,255,255,.8)">$109K - 750K · Exclusividad accesible</span></div></div>
<div class="pos-dot" style="bottom:55%;left:72%"><div class="label">Daniela Salcedo<span class="price">$450K - 900K</span></div></div>
<div class="pos-dot" style="bottom:70%;left:88%"><div class="label">Filamental<span class="price">$600K - 1.2M</span></div></div>
</div>
</section>

<!-- CICLO DE VIDA -->
<span class="chapter-label anim">Ciclo de vida</span>
<h2 class="section-title anim" style="margin-bottom:8px">Ciclo de vida — Allora</h2>
<p class="section-sub anim">Haz clic en cada fase para desplegar los detalles</p>
<div class="lifecycle-container anim d2">
  <div class="lc-wrapper">
    <div class="lc-chart">
      <div class="lc-curve">
        <svg class="lc-svg" viewBox="0 0 600 200" preserveAspectRatio="none">
          <path d="M0,185 C30,180 60,175 90,160 C120,140 150,100 180,70 C210,45 240,30 280,20 C320,12 360,10 400,15 C440,22 470,40 500,70 C530,100 560,140 600,170" fill="none" stroke="#1a3328" stroke-width="2.5"/>
          <circle cx="80" cy="165" r="8" fill="#d1fae5" stroke="#5cb89b" stroke-width="2"/>
          <circle cx="200" cy="65" r="8" fill="#fef3c7" stroke="#d97706" stroke-width="2"/>
          <circle cx="350" cy="18" r="8" fill="#ede9fe" stroke="#7c3aed" stroke-width="2"/>
          <circle cx="490" cy="60" r="8" fill="#fee2e2" stroke="#dc2626" stroke-width="2"/>
        </svg>
      </div>
    </div>
    <div class="lc-expand">
      <div class="lc-expand-card ec-intro open" onclick="toggleLC(this)"><h4 style="color:#5cb89b"><span class="lc-toggle">▾</span>Introducción</h4><div class="lc-items"><li>Inversión fuerte en branding digital</li><li>Visibilidad inicial limitada</li><li>Comunidad digital en construcción</li><li>Redes sociales como canal clave</li></div></div>
      <div class="lc-expand-card ec-growth" onclick="toggleLC(this)"><h4 style="color:#d97706"><span class="lc-toggle">▾</span>Crecimiento</h4><div class="lc-items"><li>Incremento de indicadores digitales</li><li>Aumento de notoriedad de marca</li><li>Expansión de comunidad digital</li><li>Primeras ventas recurrentes</li></div></div>
      <div class="lc-expand-card ec-maturity" onclick="toggleLC(this)"><h4 style="color:#7c3aed"><span class="lc-toggle">▾</span>Madurez</h4><div class="lc-items"><li>Consolidación de marca</li><li>Alta fidelización con comunidad</li><li>Diversificación de productos</li><li>Lifestyle activo</li></div></div>
      <div class="lc-expand-card ec-decline" onclick="toggleLC(this)"><h4 style="color:#dc2626"><span class="lc-toggle">▾</span>Reinvención</h4><div class="lc-items"><li>Caída de relevancia si no hay innovación</li><li>Necesidad de nuevas cápsulas</li><li>Relectura del simbolismo de marca</li></div></div>
    </div>
  </div>
</div>


<!-- DAFO -->
<section class="section" id="dafo">
<h3 style="font-family:'Lora',serif;font-size:24px;margin-bottom:20px" class="anim">DAFO</h3>
<div class="dafo-grid anim d2">
<div class="dafo-card strengths"><h4><span class="dot"></span>Fortalezas</h4><ul><li>Storytelling humano y diferenciador</li><li>Narrativa de evolución y ciclicidad</li><li>Conexión emocional auténtica en digital</li><li>Propuesta de valor centrada en simbolismo</li><li>Identidad visual 80s + maximalista</li></ul></div>
<div class="dafo-card weaknesses"><h4><span class="dot"></span>Debilidades</h4><ul><li>Marca en fase de introducción</li><li>Baja visibilidad inicial</li><li>Comunidad digital en construcción</li><li>Tráfico web reducido</li><li>Alta dependencia de canales digitales</li></ul></div>
<div class="dafo-card opportunities"><h4><span class="dot"></span>Oportunidades</h4><ul><li>Boom del maximalismo (tendencia 2026)</li><li>E-commerce emocional en crecimiento</li><li>Consumidor que prioriza significado</li><li>Expansión del social commerce</li><li>Diferenciación por narrativa simbólica</li></ul></div>
<div class="dafo-card threats"><h4><span class="dot"></span>Amenazas</h4><ul><li>Saturación de emprendimientos artesanales</li><li>Canibalización del concepto handmade</li><li>Costos crecientes de adquisición digital</li><li>Volatilidad de algoritmos sociales</li><li>Competencia internacional y local</li></ul></div>
</div>
</section>

<!-- CAME -->
<h3 style="font-family:'Lora',serif;font-size:24px;margin-bottom:24px" class="anim">CAME</h3>
<div class="came-matrix anim d2">
  <div class="came-matrix-wrap">
    <div class="came-matrix-header"><div class="corner"></div><div class="left">Factores internos</div><div class="right">Factores externos</div></div>
    <div class="came-matrix-body">
      <div class="side-label" style="color:#5cb89b">Positivo</div>
      <div class="came-quadrant came-m"><h4>M — Mantener fortalezas</h4><p>Capitalizar storytelling de evolución y nostalgia en cada punto digital.</p><p>Comunicar la joya como extensión de la historia personal.</p><div class="came-quote">"Un compromiso contigo misma."</div></div>
      <div class="came-quadrant came-e"><h4>E — Explotar oportunidades</h4><p>Alinear contenido visual con la tendencia del maximalismo 2026.</p><p>Usar videos cortos que resalten el simbolismo y magnitud de las piezas.</p><p>Capturar segmentos que buscan diferenciación.</p></div>
      <div class="side-label" style="color:#dc2626">Negativo</div>
      <div class="came-quadrant came-c"><h4>C — Corregir debilidades</h4><p>Implementar estrategia de contenidos que valide la propuesta de valor.</p><p>Transformar tráfico orgánico en base de datos propia.</p><p>Reducir dependencia exclusiva de algoritmos.</p><p>Generar confianza ante baja visibilidad.</p></div>
      <div class="came-quadrant came-a"><h4>A — Afrontar amenazas</h4><p>Responder a la canibalización del sector artesanal con autenticidad radical.</p><p>No competir por procesos técnicos, sino por profundidad emocional.</p><p>Cada cápsula = un momento más en el camino de evolución.</p></div>
    </div>
  </div>
</div>


<!-- Connected Chapters -->
<div class="section" style="padding-top:20px;padding-bottom:60px">
<span class="chapter-label anim" style="display:block;text-align:center;margin-bottom:16px">Sigue tu viaje</span>
<h3 class="anim" style="font-family:'Lora',serif;font-size:24px;text-align:center;margin-bottom:24px;color:var(--text)">Capítulos conectados</h3>
<div class="connected anim d2">
<a href="#producto" class="connected-link"><div><div class="lb">Explora</div><div class="title">Marketing Mix</div></div><span class="arr">→</span></a>
<a href="#pestel" class="connected-link"><div><div class="lb">Explora</div><div class="title">Análisis</div></div><span class="arr">→</span></a>
</div>
</div>

<!-- PRODUCTO -->
<section class="section" id="producto">
<span class="chapter-label anim">Capítulo 3</span>
<h2 class="section-title anim">Marketing Mix</h2>
<p class="section-sub anim">Las cuatro Ps que sostienen la propuesta de valor de Allora: producto, precio, distribución y promoción.</p>
<h3 style="font-family:'Lora',serif;font-size:24px;margin-bottom:20px" class="anim">Producto · Márgenes</h3>
<div class="data-table anim d2">
<table>
<thead><tr><th>Pieza</th><th class="num">Costo</th><th class="num">PVP</th><th class="num">Margen</th></tr></thead>
<tbody>
<tr><td>Collar Mística Ancestral</td><td class="num">€38.39</td><td class="num">€150.00</td><td class="num">74.4%</td></tr>
<tr><td>Choker Lumina</td><td class="num">€42.07</td><td class="num">€150.00</td><td class="num">72.0%</td></tr>
<tr><td>Collar Gala Imperial</td><td class="num">€42.07</td><td class="num">€172.00</td><td class="num">75.5%</td></tr>
<tr><td>Choker Corazón Sagrado</td><td class="num">€34.48</td><td class="num">€133.00</td><td class="num">74.1%</td></tr>
<tr><td>Brazalete Talismán</td><td class="num">€26.90</td><td class="num">€100.00</td><td class="num">73.1%</td></tr>
<tr><td>Pulsera Círculo Fortuna</td><td class="num">€22.76</td><td class="num">€75.00</td><td class="num">69.7%</td></tr>
<tr><td>Colección Bandana Soul</td><td class="num">€13.56</td><td class="num">€34.50</td><td class="num">60.7%</td></tr>
<tr><td>Charms Individuales</td><td class="num">€17.70</td><td class="num">€35.00</td><td class="num">49.4%</td></tr>
</tbody>
</table>
</div>
</section>

<!-- PRECIO -->
<section class="section" id="precio">
<h3 style="font-family:'Lora',serif;font-size:24px;margin-bottom:20px" class="anim">Precio</h3>
<div class="price-grid anim d2">
<div class="price-card"><div class="lb">Estrategia</div><h4>Value-based pricing</h4><p>Precios basados en valor percibido. Posicionamiento de lujo artesanal por encima de descuentos masivos.</p></div>
<div class="price-card"><div class="lb">Primera compra</div><div class="big">10%</div><p>Descuento del 10% en la primera compra como gancho de bienvenida.<br><span style="font-size:11px;color:var(--text3)">Hasta 15% adicional en Black Friday y 10% extra por programa de afiliados.</span></p></div>
<div class="price-card"><div class="lb">Valor añadido</div><h4>Reparación incluida</h4><p>El precio incluye servicio de reparación: justifica la inversión en una pieza durable.</p></div>
</div>
</section>

<!-- DISTRIBUCIÓN -->
<section class="section" id="distribucion">
<h3 style="font-family:'Lora',serif;font-size:24px;margin-bottom:20px" class="anim">Distribución</h3>
<div class="dist-grid anim d2">
<div class="dist-card"><div class="lb">D2C Online</div><h4>E-commerce exclusivo Colombia</h4><ul><li>Envíos en 2-5 días hábiles vía Servientrega / Coordinadora</li><li>Envío gratis en compras > €45 (~$200.000 COP)</li><li>Costo fijo de €4.20 en compras menores</li></ul></div>
<div class="dist-card"><div class="lb">Presencia física</div><h4>Pop-ups y ferias</h4><ul><li>Activaciones temporales en Bogotá y Medellín, ferias de diseño y experiencias inmersivas para fortalecer la conexión emocional.</li></ul></div>
</div>
</section>

<!-- PROMOCIÓN -->
<section class="section" id="promocion">
<h3 style="font-family:'Lora',serif;font-size:24px;margin-bottom:20px" class="anim">Promoción</h3>
<div class="promo-grid anim d2">
<div class="promo-card"><h4>Storytelling Digital</h4><p>Funnel general en Instagram y TikTok para construir comunidad de creyentes del amuleto.</p></div>
<div class="promo-card"><h4>Influencer Marketing</h4><p>Micro-influencers (engagement >5%) bajo modelo CPA y afiliación.</p></div>
<div class="promo-card"><h4>Email Marketing</h4><p>Flujos automatizados: carrito abandonado y fidelización con contenido exclusivo.</p></div>
</div>
</section>

<!-- Connected Chapters -->
<div class="section" style="padding-top:20px;padding-bottom:60px">
<span class="chapter-label anim" style="display:block;text-align:center;margin-bottom:16px">Sigue tu viaje</span>
<h3 class="anim" style="font-family:'Lora',serif;font-size:24px;text-align:center;margin-bottom:24px;color:var(--text)">Capítulos conectados</h3>
<div class="connected anim d2">
<a href="#resumen-digital" class="connected-link"><div><div class="lb">Explora</div><div class="title">Digital</div></div><span class="arr">→</span></a>
<a href="#simulador" class="connected-link"><div><div class="lb">Explora</div><div class="title">Finanzas</div></div><span class="arr">→</span></a>
</div>
</div>

<!-- DIGITAL -->
<section class="section" id="resumen-digital">
<span class="chapter-label anim">Capítulo 4</span>
<h2 class="section-title anim">Estrategia Digital</h2>
<p class="section-sub anim">Un viaje del consumidor en cuatro fases: del descubrimiento al amor.</p>
<div class="dig-header anim d2">
<div class="dig-stat"><div class="lb">Inversión total</div><div class="val">€100.000</div></div>
<div class="dig-stat"><div class="lb">Duración</div><div class="val">12 meses</div></div>
<div class="dig-stat"><div class="lb">ROI Total</div><div class="val" style="color:var(--primary)">278,95%</div></div>
</div>
<div class="dig-phases anim d3">
<div class="dig-phase" id="awareness">
<div class="phase">Fase 1 · Trim. 1</div><span class="budget">Presupuesto €15.000</span>
<h3>Awareness</h3>
<div class="dig-metrics">
<div class="dig-metric"><div class="lb">Visitas web</div><div class="val">11.520</div></div>
<div class="dig-metric"><div class="lb">Impresiones totales</div><div class="val">7.200.000</div></div>
<div class="dig-metric"><div class="lb">Seguidores IG+TikTok</div><div class="val">15.120</div></div>
</div>
<div class="dig-kpis"><span class="dig-kpi">CTR promedio: 1.45%</span><span class="dig-kpi">CPF total: €0.99</span><span class="dig-kpi">Tasa de rebote total: 89%</span></div>
<button class="btn-detail" onclick="openModal('awareness')">👁 Ver detalle</button>
</div>
<div class="dig-phase" id="captacion">
<div class="phase">Fase 2 · 4 meses</div><span class="budget">Presupuesto €35.000</span>
<h3>Captación</h3>
<div class="dig-metrics">
<div class="dig-metric"><div class="lb">Leads calificados</div><div class="val">10.000</div></div>
<div class="dig-metric"><div class="lb">Conversiones</div><div class="val">241</div></div>
<div class="dig-metric"><div class="lb">Ingresos fase</div><div class="val">37.958</div></div>
</div>
<div class="dig-kpis"><span class="dig-kpi">CPL promedio: €3.50</span><span class="dig-kpi">Conversión leads: 2.41%</span><span class="dig-kpi">CTR: 2.6%</span></div>
<button class="btn-detail" onclick="openModal('captacion')">👁 Ver detalle</button>
</div>
<div class="dig-phase" id="conversion">
<div class="phase">Fase 3 · 6 meses</div><span class="budget">Presupuesto €40.000</span>
<h3>Conversión</h3>
<div class="dig-metrics">
<div class="dig-metric"><div class="lb">Ventas totales</div><div class="val">1.657</div></div>
<div class="dig-metric"><div class="lb">Ingresos</div><div class="val">260.977</div></div>
<div class="dig-metric"><div class="lb">ROI</div><div class="val">552</div></div>
</div>
<div class="dig-kpis"><span class="dig-kpi">CPA promedio: €24.14</span><span class="dig-kpi">ROI conversión: 552%</span><span class="dig-kpi">Ventas Email: 864</span></div>
<button class="btn-detail" onclick="openModal('conversion')">👁 Ver detalle</button>
</div>
<div class="dig-phase" id="fidelizacion">
<div class="phase">Fase 4 · 3 meses</div><span class="budget">Presupuesto €10.000</span>
<h3>Fidelización</h3>
<div class="dig-metrics">
<div class="dig-metric"><div class="lb">Recompra</div><div class="val">25</div></div>
<div class="dig-metric"><div class="lb">Conversiones</div><div class="val">501</div></div>
<div class="dig-metric"><div class="lb">Ingresos</div><div class="val">79.320</div></div>
</div>
<div class="dig-kpis"><span class="dig-kpi">Interacción social: 35%</span><span class="dig-kpi">Conversión email: 15%</span><span class="dig-kpi">ROI: 693%</span></div>
<button class="btn-detail" onclick="openModal('fidelizacion')">👁 Ver detalle</button>
</div>
</div>
</section>

<!-- Funnel General -->
<section class="section" id="funnel-general" style="padding-top:0">
<h3 style="font-family:'Lora',serif;font-size:24px;margin-bottom:24px" class="anim">Funnel general</h3>
<div class="anim d2">
<div class="funnel-bar"><div class="name">Awareness</div><div class="bar" style="width:15%">€15.000</div></div>
<div class="funnel-bar"><div class="name">Captación</div><div class="bar" style="width:35%">€35.000</div></div>
<div class="funnel-bar"><div class="name">Conversión</div><div class="bar" style="width:40%">€40.000</div></div>
<div class="funnel-bar"><div class="name">Fidelización</div><div class="bar" style="width:10%">€10.000</div></div>
</div>
</section>

<!-- Connected Chapters -->
<div class="section" style="padding-top:20px;padding-bottom:60px">
<span class="chapter-label anim" style="display:block;text-align:center;margin-bottom:16px">Sigue tu viaje</span>
<h3 class="anim" style="font-family:'Lora',serif;font-size:24px;text-align:center;margin-bottom:24px;color:var(--text)">Capítulos conectados</h3>
<div class="connected anim d2">
<a href="#producto" class="connected-link"><div><div class="lb">Explora</div><div class="title">Marketing Mix</div></div><span class="arr">→</span></a>
<a href="#simulador" class="connected-link"><div><div class="lb">Explora</div><div class="title">Finanzas</div></div><span class="arr">→</span></a>
</div>
</div>
<section class="section" id="panel" style="padding-top:0">
  <h3 style="font-family:'Lora',serif;font-size:24px;margin-bottom:8px" class="anim">Panel de Presupuesto MKT Digital</h3>
  <p class="section-sub anim" style="margin-bottom:24px">Dashboard del presupuesto anual de marketing digital · Año 2026</p>
  <div class="fin-stats anim d2" style="grid-template-columns:repeat(4,1fr)">
    <div class="fin-stat"><div class="lb">Total Ingresos</div><div class="val" style="color:var(--primary)">€378.957</div></div>
    <div class="fin-stat"><div class="lb">Total Costes MKT</div><div class="val" style="color:#dc2626">€100.000</div></div>
    <div class="fin-stat"><div class="lb">ROI MKT</div><div class="val" style="color:var(--primary)">278.96%</div></div>
    <div class="fin-stat"><div class="lb">ROAS</div><div class="val" style="color:var(--primary)">5.53×</div></div>
  </div>
  <div class="data-table anim d3" style="margin-top:24px">
    <div style="padding:16px 20px;font-family:'Lora',serif;font-size:16px;color:var(--text);border-bottom:1px solid rgba(92,184,155,.1);display:flex;justify-content:space-between;align-items:center">
      <span>Presupuesto MKT Digital 2026 · Desglose por fase</span>
      <span style="font-size:12px;color:var(--text3)">€100.000 total</span>
    </div>
    <table>
      <thead><tr><th>Fase</th><th>Presupuesto</th><th>% del Total</th><th>Objetivo</th><th>KPI Principal</th></tr></thead>
      <tbody>
        <tr><td><strong>Awareness</strong></td><td class="num">€15.000</td><td class="num">15%</td><td>Tráfico web, impresiones</td><td class="num">7.2M imp.</td></tr>
        <tr><td><strong>Captación</strong></td><td class="num">€35.000</td><td class="num">35%</td><td>Leads cualificados</td><td class="num">10.000 leads</td></tr>
        <tr><td><strong>Conversión</strong></td><td class="num">€40.000</td><td class="num">40%</td><td>Ventas, ingresos</td><td class="num">1.657 ventas</td></tr>
        <tr><td><strong>Fidelización</strong></td><td class="num">€10.000</td><td class="num">10%</td><td>Recompra, engagement</td><td class="num">25% recompra</td></tr>
        <tr style="background:rgba(92,184,155,.08)"><td><strong>TOTAL</strong></td><td class="num"><strong>€100.000</strong></td><td class="num"><strong>100%</strong></td><td></td><td class="num"><strong>ROI 278.96%</strong></td></tr>
      </tbody>
    </table>
  </div>
</section>

      }
    ]
  },
  {
    "title": "Resultado global",
    "eyebrow": "Ingresos, costes, utilidad y ROI",
    "tone": "slate",
    "rows": [
      {
        "concepto": "Total ingresos",
        "valores": [
          "",
          "",
          "€701,60",
          "€3.465,00",
          "€6.300,00",
          "€ 8.032,50",
          "€54.495,00",
          "€48.037,50",
          "€33.862,50",
          "€61.056,75",
          "€70.269,00",
          "€92.737,50",
          "€378.957,35",
          "€947.393,38",
          "€1.610.568,74"
        ]
      },
      {
        "concepto": "Total costes V + F",
        "valores": [
          "€14.430,00",
          "€15.920,00",
          "€14.740,00",
          "€32.763,77",
          "€29.596,00",
          "€11.993,77",
          "€50.494,05",
          "€30.083,00",
          "€32.245,31",
          "€52.281,10",
          "€47.249,00",
          "€23.624,00",
          "€355.420",
          "€656.820",
          "€ 1.030.584,00"
        ]
      },
      {
        "concepto": "Utilidad",
        "valores": [
          "-€14.430,00",
          "-€15.920,00",
          "-€14.038,40",
          "-€29.298,77",
          "-€23.296,00",
          "-€ 3.961,27",
          "€4.000,95",
          "€17.954,50",
          "€1.617,19",
          "€8.775,65",
          "€23.020,00",
          "€69.113,50",
          "€23.537,35",
          "€290.573,38",
          "€579.984,74"
        ]
      },
      {
        "concepto": "ROI",
        "valores": [
          "-100,00%",
          "-100,00%",
          "-95,24%",
          "-89,42%",
          "-78,71%",
          "-33,03%",
          "7,92%",
          "59,68%",
          "5,02%",
          "16,79%",
          "48,72%",
          "292,56%",
          "6,62%",
          "44,24%",
          "56,28%"
        ]
      }
    ]
  }
];

      const iconSvg = '<svg viewBox="0 0 24 24" width="20" height="20" aria-hidden="true"><path fill="currentColor" d="M4 19h16v2H4v-2Zm1-4h3V7H5v8Zm5 0h3V3h-3v12Zm5 0h3v-5h-3v5Z"/></svg>';
      const chevronSvg = '<svg class="dmkt-block__chevron" viewBox="0 0 24 24" aria-hidden="true"><path fill="currentColor" d="M7.41 8.59 12 13.17l4.59-4.58L18 10l-6 6-6-6 1.41-1.41Z"/></svg>';
      const accordion = root.querySelector('[data-dmkt-accordion]');

      const clean = (value) => value && value.trim() ? value : '—';
      const isTotalRow = (label) => /^(TOTAL|Total ingresos|Total costes|Utilidad|ROI)/.test(label);
      const tdClass = (value, index) => [!value ? 'dmkt-table__empty' : '', index >= 12 ? 'dmkt-table__year' : ''].filter(Boolean).join(' ');

      function tableFor(group) {
        const head = columns.map((column) => `<th scope="col">${column}</th>`).join('');
        const body = group.rows.map((row) => `
          <tr class="${isTotalRow(row.concepto) ? 'dmkt-table__total-row' : ''}">
            <td class="dmkt-table__concept">${row.concepto}</td>
            ${row.valores.map((value, index) => `<td class="${tdClass(value, index)}">${clean(value)}</td>`).join('')}
          </tr>`).join('');
        return `<div class="dmkt-table-wrap"><table class="dmkt-table"><thead><tr><th scope="col">Concepto</th>${head}</tr></thead><tbody>${body}</tbody></table></div>`;
      }

      function setOpen(block, open) {
        const content = block.querySelector('.dmkt-block__content');
        const button = block.querySelector('.dmkt-block__toggle');
        block.classList.toggle('is-open', open);
        button.setAttribute('aria-expanded', String(open));
        content.style.maxHeight = open ? `${content.scrollHeight}px` : '0px';
      }

      accordion.innerHTML = groups.map((group, index) => {
        const total2026 = group.rows[group.rows.length - 1]?.valores[12] || '';
        return `
          <article class="dmkt-block ${index === 0 ? 'is-open' : ''}" data-tone="${group.tone}">
            <button class="dmkt-block__toggle" type="button" aria-expanded="${index === 0 ? 'true' : 'false'}">
              <span class="dmkt-block__icon">${iconSvg}</span>
              <span><span class="dmkt-block__title">${group.title}</span><span class="dmkt-block__eyebrow">${group.eyebrow}</span></span>
              <span class="dmkt-block__total">${clean(total2026)}</span>
              ${chevronSvg}
            </button>
            <div class="dmkt-block__content"><div class="dmkt-block__inner">${tableFor(group)}</div></div>
          </article>`;
      }).join('');

      root.querySelectorAll('.dmkt-block').forEach((block) => {
        const isOpen = block.classList.contains('is-open');
        setOpen(block, isOpen);
        block.querySelector('.dmkt-block__toggle').addEventListener('click', () => setOpen(block, !block.classList.contains('is-open')));
      });

      root.querySelector('[data-dmkt-expand]').addEventListener('click', () => root.querySelectorAll('.dmkt-block').forEach((block) => setOpen(block, true)));
      root.querySelector('[data-dmkt-collapse]').addEventListener('click', () => root.querySelectorAll('.dmkt-block').forEach((block) => setOpen(block, false)));
      window.addEventListener('resize', () => root.querySelectorAll('.dmkt-block.is-open').forEach((block) => setOpen(block, true)));
    })();
  </script>
</section>


<!-- FINANZAS -->
<section class="section" id="simulador">
<span class="chapter-label anim">Capítulo 5</span>
<h2 class="section-title anim">Análisis financiero</h2>
<p class="section-sub anim">Punto de equilibrio, simulador interactivo y proyecciones de crecimiento 2026-2028.</p>
<div class="fin-stats anim d2">
<div class="fin-stat"><div class="lb">Costos fijos</div><div class="val">€200.370</div></div>
<div class="fin-stat"><div class="lb">Precio promedio</div><div class="val">€151.58</div></div>
<div class="fin-stat"><div class="lb">Costo variable</div><div class="val">€62.02</div></div>
<div class="fin-stat"><div class="lb">Punto de equilibrio</div><div class="val">2.237 u.</div></div>
</div>
</section>

<!-- Simulador -->
<section class="section" id="simulador-full" style="padding-top:0">
<h3 style="font-family:'Lora',serif;font-size:24px;margin-bottom:8px" class="anim">Simulador de rentabilidad</h3>
<p class="section-sub anim">El punto rosa marca la posición real de Allora. Mueve los sliders y usa Reiniciar para volver a los datos del plan.</p>
<div class="sim-grid anim d2">
<div class="sim-controls">
<h3>VARIABLES</h3>
<p class="sub">Mueve los sliders y observa el impacto en tiempo real.</p>
<button class="btn-reset" onclick="resetSim()">↻ Reiniciar</button>
<div class="sim-row">
<div class="top"><span class="name">Unidades vendidas</span><span class="val" id="simUnitsVal">2.500</span></div>
<span class="real">Allora real: 2.500</span>
<input type="range" class="sim-slider" id="simUnits" min="500" max="10000" value="2500" style="--progress:20%" oninput="updateSim()">
</div>
<div class="sim-row">
<div class="top"><span class="name">Precio promedio</span><span class="val" id="simPriceVal">€152</span></div>
<span class="real">Allora real: €152</span>
<input type="range" class="sim-slider" id="simPrice" min="50" max="400" value="152" style="--progress:30%" oninput="updateSim()">
</div>
<div class="sim-row">
<div class="top"><span class="name">Costo variable / unidad</span><span class="val" id="simCostVal">€62</span></div>
<span class="real">Allora real: €62</span>
<input type="range" class="sim-slider" id="simCost" min="10" max="200" value="62" style="--progress:25%" oninput="updateSim()">
</div>
<div class="sim-summary">
<div class="sim-sum-item"><div class="lb">Unidades</div><div class="val" id="simSumUnits">2.500</div></div>
<div class="sim-sum-item"><div class="lb">Precio prom.</div><div class="val" id="simSumPrice">€152</div></div>
<div class="sim-sum-item"><div class="lb">Costo var.</div><div class="val" id="simSumCost">€62</div></div>
</div>
</div>
<div class="sim-results">
<div class="sim-result"><div class="lb">Ingresos</div><div class="val" id="simIngresos">€380.000</div></div>
<div class="sim-result"><div class="lb">Utilidad</div><div class="val" id="simUtilidad">€24.630</div></div>
<div class="sim-result"><div class="lb">Margen neto</div><div class="val" id="simMargen">6.5%</div></div>
<div class="sim-result"><div class="lb">Punto de equilibrio</div><div class="val" id="simBE">2.227 u.</div></div>
</div>
</div>
</section>

<!-- Break Even -->
<section class="section" id="break-even" style="padding-top:0">
<h3 style="font-family:'Lora',serif;font-size:24px;margin-bottom:8px" class="anim">Punto de equilibrio</h3>
<p class="section-sub anim">La línea fucsia marca dónde está Allora hoy (2.500 unidades). Está por encima del punto de equilibrio (2.237 u.) → genera beneficio.</p>
<div class="chart-container anim d2" id="breakEvenChart"></div>
</section>

<!-- Proyecciones -->
<section class="section" id="proyecciones" style="padding-top:0">
<h3 style="font-family:'Lora',serif;font-size:24px;margin-bottom:24px" class="anim">Proyecciones 2026 — 2028</h3>
<div class="proj-grid anim d2">
<div class="proj-chart" id="projChart"></div>
<div class="proj-cards">
<div class="proj-card">
<div class="year">2026</div>
<div class="info">
<div class="row"><span>Ingresos</span><span>€378.957</span></div>
<div class="row"><span>Utilidad</span><span>€23.537</span></div>
<div class="row"><span>ROI</span><span>6.62%</span></div>
</div>
<div class="bar-wrap"><div class="bar-fill" style="width:15%"></div></div>
<button class="btn-detail" onclick="openModal('detalle2026')" style="margin-top:8px">👁 Ver detalle</button>
</div>
<div class="proj-card">
<div class="year">2027</div>
<div class="info">
<div class="row"><span>Ingresos</span><span>€947.393</span></div>
<div class="row"><span>Utilidad</span><span>€290.573</span></div>
<div class="row"><span>ROI</span><span>44.24%</span></div>
</div>
<div class="bar-wrap"><div class="bar-fill" style="width:45%"></div></div>
</div>
<div class="proj-card">
<div class="year">2028</div>
<div class="info">
<div class="row"><span>Ingresos</span><span>€1.610.569</span></div>
<div class="row"><span>Utilidad</span><span>€579.985</span></div>
<div class="row"><span>ROI</span><span>56.28%</span></div>
</div>
<div class="bar-wrap"><div class="bar-fill" style="width:75%"></div></div>
</div>
</div>
</div>
</section>

<!-- Unidades por año -->
<section class="section" id="unidades" style="padding-top:0">
<h3 style="font-family:'Lora',serif;font-size:24px;margin-bottom:8px" class="anim">Unidades por año</h3>
<p class="section-sub anim">Cada año conecta con el desglose de mercado TAM · SAM · SOM.</p>
<div class="bar-chart anim d2">
<div style="position:relative;height:220px">
<div style="position:absolute;left:0;top:0;bottom:30px;width:40px;display:flex;flex-direction:column;justify-content:space-between;font-size:11px;color:var(--text3)"><span>12000</span><span>9000</span><span>6000</span><span>3000</span><span>0</span></div>
<div style="position:absolute;left:50px;right:20px;top:0;bottom:30px;display:flex;align-items:flex-end;gap:24px">
<div style="flex:1;display:flex;flex-direction:column;align-items:center;gap:4px">
<div style="width:100%;background:var(--primary);border-radius:8px 8px 0 0;height:50px;position:relative;cursor:pointer" onmouseenter="showBarTooltip(this,'2026','2.500')" onmouseleave="hideBarTooltip()">
</div><span style="font-size:11px;color:var(--text3)">2026</span></div>
<div style="flex:1;display:flex;flex-direction:column;align-items:center;gap:4px">
<div style="width:100%;background:var(--primary);border-radius:8px 8px 0 0;height:120px;position:relative;cursor:pointer" onmouseenter="showBarTooltip(this,'2027','6.250')" onmouseleave="hideBarTooltip()"></div><span style="font-size:11px;color:var(--text3)">2027</span></div>
<div style="flex:1;display:flex;flex-direction:column;align-items:center;gap:4px">
<div style="width:100%;background:var(--primary);border-radius:8px 8px 0 0;height:190px;position:relative;cursor:pointer" onmouseenter="showBarTooltip(this,'2028','10.625')" onmouseleave="hideBarTooltip()"></div><span style="font-size:11px;color:var(--text3)">2028</span></div>
</div>
<div id="barTooltip" style="position:absolute;display:none;background:rgba(255,255,255,.95);backdrop-filter:blur(10px);padding:10px 16px;border-radius:12px;box-shadow:0 4px 20px rgba(0,0,0,.1);z-index:10;pointer-events:none">
<div style="font-size:11px;font-weight:600;color:var(--text)" id="barTooltipYear"></div>
<div style="font-size:12px;color:var(--primary)" id="barTooltipVal"></div>
</div>
</div>
</div>
<div style="display:grid;grid-template-columns:repeat(3,1fr);gap:16px;margin-top:16px" class="anim d3">
<div class="glass-card" style="display:flex;align-items:center;justify-content:space-between">
<div><div style="font-size:10px;font-weight:600;letter-spacing:2px;text-transform:uppercase;color:var(--primary)">Año 2026</div><div style="font-family:'Lora',serif;font-size:24px;color:var(--text);margin:4px 0">2.500</div><div style="font-size:12px;color:var(--text3)">unidades proyectadas</div></div>
<button class="btn-detail" onclick="openModal('tam2026')">👁 Ver detalle</button>
</div>
<div class="glass-card" style="display:flex;align-items:center;justify-content:space-between">
<div><div style="font-size:10px;font-weight:600;letter-spacing:2px;text-transform:uppercase;color:var(--primary)">Año 2027</div><div style="font-family:'Lora',serif;font-size:24px;color:var(--text);margin:4px 0">6.250</div><div style="font-size:12px;color:var(--text3)">unidades proyectadas</div></div>
<button class="btn-detail" onclick="openModal('tam2027')">👁 Ver detalle</button>
</div>
<div class="glass-card" style="display:flex;align-items:center;justify-content:space-between">
<div><div style="font-size:10px;font-weight:600;letter-spacing:2px;text-transform:uppercase;color:var(--primary)">Año 2028</div><div style="font-family:'Lora',serif;font-size:24px;color:var(--text);margin:4px 0">10.625</div><div style="font-size:12px;color:var(--text3)">unidades proyectadas</div></div>
<button class="btn-detail" onclick="openModal('tam2028')">👁 Ver detalle</button>
</div>
</div>
</section>

<!-- Resultados generales -->
<section class="section" id="resultados" style="padding-top:0">
<h3 style="font-family:'Lora',serif;font-size:24px;margin-bottom:8px" class="anim">Resultados generales · 2026</h3>
<p class="section-sub anim">Resumen visual del P&L del primer año. Datos reales del plan financiero sin reinterpretación.</p>
<div class="fin-stats anim d2" style="grid-template-columns:repeat(4,1fr)">
<div class="fin-stat"><div class="lb">Total Ingresos</div><div class="val">€378.957</div><div style="font-size:11px;color:var(--text3);margin-top:4px">2.403 ventas · ticket €151.58</div></div>
<div class="fin-stat"><div class="lb">Total Costes</div><div class="val">€155.050</div><div style="font-size:11px;color:var(--text3);margin-top:4px">Producción de 2.500 piezas</div></div>
<div class="fin-stat"><div class="lb">Total Gastos</div><div class="val">€200.370</div><div style="font-size:11px;color:var(--text3);margin-top:4px">Operación + marketing + estructura</div></div>
<div class="fin-stat"><div class="lb">Utilidad Neta</div><div class="val" style="color:var(--primary)">↗ €23.537</div><div style="font-size:11px;color:var(--text3);margin-top:4px">ROI 6.62% · margen 6.21%</div></div>
</div>
<div class="pl-chart anim d3" id="plChart" style="margin-top:24px"></div>
<div style="display:grid;grid-template-columns:1fr 1fr;gap:20px;margin-top:20px" class="anim d4">
<div class="glass-card">
<h4 style="font-family:'Lora',serif;font-size:18px;color:var(--text);margin-bottom:16px">Origen de los ingresos</h4>
<div style="margin-bottom:14px"><div style="display:flex;justify-content:space-between;font-size:13px;margin-bottom:4px"><span style="color:var(--text);font-weight:500">E-commerce</span><span style="color:var(--text)">€279.391</span></div><div style="height:6px;background:rgba(92,184,155,.15);border-radius:3px"><div style="height:100%;width:73.7%;background:var(--primary);border-radius:3px"></div></div><div style="font-size:11px;color:var(--text3);margin-top:2px">1.753 ventas · 73.7%</div></div>
<div style="margin-bottom:14px"><div style="display:flex;justify-content:space-between;font-size:13px;margin-bottom:4px"><span style="color:var(--text);font-weight:500">Recompras</span><span style="color:var(--text)">€47.749</span></div><div style="height:6px;background:rgba(92,184,155,.15);border-radius:3px"><div style="height:100%;width:12.6%;background:var(--primary);border-radius:3px"></div></div><div style="font-size:11px;color:var(--text3);margin-top:2px">321 ventas · 12.6%</div></div>
<div><div style="display:flex;justify-content:space-between;font-size:13px;margin-bottom:4px"><span style="color:var(--text);font-weight:500">Afiliación</span><span style="color:var(--text)">€51.818</span></div><div style="height:6px;background:rgba(92,184,155,.15);border-radius:3px"><div style="height:100%;width:13.7%;background:var(--primary);border-radius:3px"></div></div><div style="font-size:11px;color:var(--text3);margin-top:2px">329 ventas · 13.7%</div></div>
</div>
<div class="glass-card">
<h4 style="font-family:'Lora',serif;font-size:18px;color:var(--text);margin-bottom:16px">Costes de producción</h4>
<div style="margin-bottom:12px"><div style="display:flex;justify-content:space-between;font-size:13px;margin-bottom:4px"><span style="color:var(--text);font-weight:500">Metales y materias primas</span><span style="color:var(--text)">€85.000</span></div><div style="height:6px;background:rgba(92,184,155,.15);border-radius:3px"><div style="height:100%;width:54.8%;background:var(--primary);border-radius:3px"></div></div></div>
<div style="margin-bottom:12px"><div style="display:flex;justify-content:space-between;font-size:13px;margin-bottom:4px"><span style="color:var(--text);font-weight:500">Mano de obra</span><span style="color:var(--text)">€27.500</span></div><div style="height:6px;background:rgba(92,184,155,.15);border-radius:3px"><div style="height:100%;width:17.7%;background:var(--primary);border-radius:3px"></div></div></div>
<div style="margin-bottom:12px"><div style="display:flex;justify-content:space-between;font-size:13px;margin-bottom:4px"><span style="color:var(--text);font-weight:500">Packaging</span><span style="color:var(--text)">€20.000</span></div><div style="height:6px;background:rgba(92,184,155,.15);border-radius:3px"><div style="height:100%;width:12.9%;background:var(--primary);border-radius:3px"></div></div></div>
<div style="margin-bottom:12px"><div style="display:flex;justify-content:space-between;font-size:13px;margin-bottom:4px"><span style="color:var(--text);font-weight:500">Logísticos</span><span style="color:var(--text)">€22.000</span></div><div style="height:6px;background:rgba(92,184,155,.15);border-radius:3px"><div style="height:100%;width:14.2%;background:var(--primary);border-radius:3px"></div></div></div>
<div><div style="display:flex;justify-content:space-between;font-size:13px;margin-bottom:4px"><span style="color:var(--text);font-weight:500">Servicio de reparación</span><span style="color:var(--text)">€550</span></div><div style="height:6px;background:rgba(92,184,155,.15);border-radius:3px"><div style="height:100%;width:0.4%;background:var(--primary);border-radius:3px"></div></div></div>
</div>
</div>
<div class="bar-chart anim d5" style="margin-top:20px">
<h3>Top 10 gastos</h3>
<div class="bar-row"><div class="name">Salarios</div><div class="bar"><div class="fill" style="width:95%">€76.800</div></div></div>
<div class="bar-row"><div class="name">Paid Media (TT+IG)</div><div class="bar"><div class="fill" style="width:41%">€32.350</div></div></div>
<div class="bar-row"><div class="name">Marketing afiliación</div><div class="bar"><div class="fill" style="width:22%">€17.050</div></div></div>
<div class="bar-row"><div class="name">Mailchimp</div><div class="bar"><div class="fill" style="width:22%">€17.200</div></div></div>
<div class="bar-row"><div class="name">Alquiler</div><div class="bar"><div class="fill" style="width:16%">€12.000</div></div></div>
<div class="bar-row"><div class="name">Herramientas automatización</div><div class="bar"><div class="fill" style="width:11%">€7.650</div></div></div>
<div class="bar-row"><div class="name">Influencer marketing</div><div class="bar"><div class="fill" style="width:7%">€5.000</div></div></div>
<div class="bar-row"><div class="name">Seguro de joya</div><div class="bar"><div class="fill" style="width:6%">€5.000</div></div></div>
<div class="bar-row"><div class="name">Google Ads</div><div class="bar"><div class="fill" style="width:6%">€4.840</div></div></div>
<div class="bar-row"><div class="name">Asesoría legal y fiscal</div><div class="bar"><div class="fill" style="width:4%">€3.000</div></div></div>
</div>
<div class="data-table anim d6" style="margin-top:20px">
<div style="padding:16px 20px;font-family:'Lora',serif;font-size:16px;color:var(--text);border-bottom:1px solid rgba(92,184,155,.1)">Detalle mensual 2026</div>
<table class="monthly-table">
<thead><tr><th>Mes</th><th>Ingresos</th><th>Egresos</th><th>Utilidad</th><th>ROI</th></tr></thead>
<tbody>
<tr><td>Ene</td><td>€0</td><td>€14.430</td><td class="neg">€-14.430</td><td class="neg">-100.0%</td></tr>
<tr><td>Feb</td><td>€0</td><td>€15.920</td><td class="neg">€-15.920</td><td class="neg">-100.0%</td></tr>
<tr><td>Mar</td><td>€702</td><td>€14.740</td><td class="neg">€-14.038</td><td class="neg">-95.2%</td></tr>
<tr><td>Abr</td><td>€3.465</td><td>€35.264</td><td class="neg">€-31.799</td><td class="neg">-90.2%</td></tr>
<tr><td>May</td><td>€6.300</td><td>€18.736</td><td class="neg">€-12.436</td><td class="neg">-66.4%</td></tr>
<tr><td>Jun</td><td>€8.033</td><td>€11.994</td><td class="neg">€-3.961</td><td class="neg">-33.0%</td></tr>
<tr><td>Jul</td><td>€54.495</td><td>€49.494</td><td class="pos">€5.001</td><td class="pos">10.1%</td></tr>
<tr><td>Ago</td><td>€48.038</td><td>€30.083</td><td class="pos">€17.955</td><td class="pos">59.7%</td></tr>
<tr><td>Sep</td><td>€33.863</td><td>€32.124</td><td class="pos">€1.738</td><td class="pos">5.4%</td></tr>
<tr><td>Oct</td><td>€61.057</td><td>€52.281</td><td class="pos">€8.776</td><td class="pos">16.8%</td></tr>
<tr><td>Nov</td><td>€70.269</td><td>€47.249</td><td class="pos">€23.020</td><td class="pos">48.7%</td></tr>
<tr><td>Dic</td><td>€92.738</td><td>€32.624</td><td class="pos">€60.114</td><td class="pos">184.3%</td></tr>
<tr><td><b>Total</b></td><td><b>€378.957</b></td><td><b>€355.420</b></td><td><b class="pos">€23.537</b></td><td><b class="pos">6.62%</b></td></tr>
</tbody>
</table>
</div>
</section>

<!-- Connected Chapters -->
<div class="section" style="padding-top:20px;padding-bottom:60px">
<span class="chapter-label anim" style="display:block;text-align:center;margin-bottom:16px">Sigue tu viaje</span>
<h3 class="anim" style="font-family:'Lora',serif;font-size:24px;text-align:center;margin-bottom:24px;color:var(--text)">Capítulos conectados</h3>
<div class="connected anim d2">
<a href="#resumen-digital" class="connected-link"><div><div class="lb">Explora</div><div class="title">Digital</div></div><span class="arr">→</span></a>
<a href="#cadena" class="connected-link"><div><div class="lb">Explora</div><div class="title">Estrategia</div></div><span class="arr">→</span></a>
</div>
</div>

</div><!-- end content -->

<!-- MODAL -->
<div class="modal-overlay" id="modalOverlay">
<div class="modal" id="modalContent"></div>
</div>

<!-- CONSTELLATION MAP MODAL -->
<div class="modal-overlay" id="mapOverlay">
<div class="modal" style="max-width:500px;padding:36px">
<button class="modal-close" onclick="closeMap()">✕</button>
<h2 style="font-family:'Lora',serif;font-size:22px;margin-bottom:4px">Tu mapa</h2>
<p style="font-size:12px;color:var(--text3);margin-bottom:24px">Cada constelación es un capítulo de Allora</p>
<div class="constellation">
<svg viewBox="0 0 400 400" style="position:absolute;top:0;left:0">
<line x1="200" y1="60" x2="80" y2="180" stroke="rgba(92,184,155,.15)" stroke-width="1"/>
<line x1="200" y1="60" x2="320" y2="180" stroke="rgba(92,184,155,.15)" stroke-width="1"/>
<line x1="80" y1="180" x2="120" y2="320" stroke="rgba(92,184,155,.15)" stroke-width="1"/>
<line x1="120" y1="320" x2="200" y2="360" stroke="rgba(92,184,155,.15)" stroke-width="1"/>
<line x1="200" y1="360" x2="280" y2="320" stroke="rgba(92,184,155,.15)" stroke-width="1"/>
<line x1="280" y1="320" x2="320" y2="180" stroke="rgba(92,184,155,.15)" stroke-width="1"/>
<line x1="320" y1="180" x2="200" y2="60" stroke="rgba(92,184,155,.15)" stroke-width="1"/>
<line x1="80" y1="180" x2="320" y2="180" stroke="rgba(92,184,155,.1)" stroke-width="1"/>
<line x1="120" y1="320" x2="280" y2="320" stroke="rgba(92,184,155,.1)" stroke-width="1"/>
</svg>
<a href="#inicio" class="const-dot" style="top:20px;left:50%;transform:translateX(-50%)" onclick="closeMap()"><span class="letter">I</span><span class="name">Inicio</span></a>
<a href="#pestel" class="const-dot" style="top:140px;left:10px" onclick="closeMap()"><span class="letter">A</span><span class="name">Análisis</span></a>
<a href="#cadena" class="const-dot" style="top:140px;right:10px" onclick="closeMap()"><span class="letter">E</span><span class="name">Estrategia</span></a>
<a href="#producto" class="const-dot" style="bottom:50px;left:40px" onclick="closeMap()"><span class="letter">M</span><span class="name">Marketing Mix</span></a>
<a href="#resumen-digital" class="const-dot" style="bottom:50px;right:40px" onclick="closeMap()"><span class="letter">D</span><span class="name">Digital</span></a>
<a href="#simulador" class="const-dot" style="bottom:10px;left:50%;transform:translateX(-50%)" onclick="closeMap()"><span class="letter">F</span><span class="name">Finanzas</span></a>
</div>
</div>
</div>

<script>
// Dropdown
const ddOverlay=document.getElementById('ddOverlay');
const navBtns=document.querySelectorAll('.nav-btn');
let activeDd=null;

function closeAllDd(){
  navBtns.forEach(b=>b.classList.remove('active'));
  document.querySelectorAll('.dd').forEach(d=>d.classList.remove('show'));
  ddOverlay.classList.remove('show');
  activeDd=null;
}

navBtns.forEach(btn=>{
  btn.addEventListener('click',e=>{
    e.preventDefault();e.stopPropagation();
    const id=btn.getAttribute('data-dd');
    const dd=document.getElementById(id);
    if(activeDd===dd){closeAllDd();return;}
    closeAllDd();
    btn.classList.add('active');
    dd.classList.add('show');
    ddOverlay.classList.add('show');
    activeDd=dd;
  });
});
ddOverlay.addEventListener('click',closeAllDd);

// Quiz
const quizData=[
  {q:'Cuando eliges una joya, lo primero que te atrae es...',opts:['Su diseño artesanal y la historia detrás','El momento o persona a quien quiero honrar','Su simbolismo y la energía que transmite']},
  {q:'Tu ritual de mañana incluye...',opts:['Curar mi feed de Instagram con referencias visuales','Revisar la agenda y planear la jornada con propósito','Respirar, meditar o elegir mi intención del día']},
  {q:'¿Qué significa para ti llevar una joya?',opts:['Un gesto estético que completa mi identidad','Un recordatorio de alguien o algo importante','Un talismán que me protege y alinea']},
  {q:'Tu paleta de vida se parece más a...',opts:['Tonos tierra, texturas nobles y luz natural','Neutros elegantes y detalles brillantes','Lilas, plateados y destellos místicos']},
  {q:'Si tuvieras que describir tu joya ideal en una palabra...',opts:['Artesanía','Significado','Amuleto']}
];
let quizStep=0;
let quizAnswers=[];

function renderQuiz(){
  const card=document.getElementById('quizCard');
  if(quizStep>=quizData.length){
    // Result
    const profiles=[
      {name:'Sandra',sub:'La Estética Consciente',desc:'Valora lo hecho a mano, el consumo consciente y la historia detrás de cada pieza. Descubre en redes proyectos independientes y aprecia la transparencia.',mot:'Expresión estética personal y aprecio por la artesanía.',piece:'Collar Mística Ancestral'},
      {name:'Valentina',sub:'La Narrativa Emocional',desc:'Cada joya es un recuerdo, un vínculo con alguien especial. Busca piezas que cuenten historias y honren momentos significativos.',mot:'Honrar momentos y personas a través de símbolos.',piece:'Choker Corazón Sagrado'},
      {name:'Camila',sub:'La Mística Digital',desc:'Conectada con lo espiritual y lo ancestral. Busca amuletos que la protejan y alineen con su energía. El simbolismo es su lenguaje.',mot:'Protección, alineación energética y ritual personal.',piece:'Brazalete Talismán'}
    ];
    const a=quizAnswers.reduce((s,v)=>s+v,0);
    const p=a<=4?profiles[0]:a<=8?profiles[1]:profiles[2];
    card.innerHTML=`<div class="quiz-result">
      <div class="quiz-label">✨ Tu amuleto</div>
      <h3>Eres ${p.name}</h3>
      <div class="sub">${p.sub}</div>
      <p>${p.desc}</p>
      <div class="quiz-result-boxes">
        <div class="quiz-rbox"><div class="lb">Motivación</div><div class="val">${p.mot}</div></div>
        <div class="quiz-rbox"><div class="lb">Tu pieza</div><div class="val">${p.piece}</div></div>
      </div>
      <div class="quiz-btns">
        <button class="btn-small btn-green" onclick="quizStep=0;quizAnswers=[];renderQuiz()">Continuar mi viaje →</button>
        <button class="btn-small btn-ghost" onclick="quizStep=0;quizAnswers=[];renderQuiz()">↻ Reiniciar</button>
      </div>
    </div>`;
    return;
  }
  const d=quizData[quizStep];
  card.innerHTML=`<div class="quiz-label">✨ Pregunta ${quizStep+1} de 5</div>
    <div class="quiz-progress">${quizData.map((_,i)=>`<div class="bar${i<quizStep?' done':''}"></div>`).join('')}</div>
    <div class="quiz-q">${d.q}</div>
    ${d.opts.map((o,i)=>`<button class="quiz-opt${quizAnswers[quizStep]===i?' selected':''}" onclick="selectQuiz(${i})">${o}<span class="arr">→</span></button>`).join('')}`;
}

function selectQuiz(i){
  quizAnswers[quizStep]=i;
  quizStep++;
  renderQuiz();
}

renderQuiz();

// TAM
function showTam(type){
  document.querySelectorAll('.tam-card').forEach(c=>c.classList.remove('active'));
  event.currentTarget.classList.add('active');
  const data={
    tam:{lb:'TAM · Mercado total Bogotá',amount:'€247.000.000',text:'Consumo anual de joyería en Bogotá estimado en torno a 247 millones de euros.'},
    sam:{lb:'SAM · Mercado disponible',amount:'€209.000.000',text:'1.159.200 piezas anuales: 579.600 mujeres que compran 2 veces al año. ~13% del TAM.'},
    som:{lb:'SOM · Objetivo año 1',amount:'€378.957',text:'2.500 piezas anuales, objetivo realista para los primeros 12 meses; proyección a 6.250 piezas (€947.393) en 24 meses.'}
  };
  const d=data[type];
  document.getElementById('tamDetailLb').textContent=d.lb;
  document.getElementById('tamDetailAmount').textContent=d.amount;
  document.getElementById('tamDetailText').textContent=d.text;
}

// PESTEL
function showPestel(type){
  document.querySelectorAll('.pestel-item').forEach(c=>c.classList.remove('active'));
  event.currentTarget.classList.add('active');
  const data={
    p:{h3:'Político',h4:'Estabilidad moderada y polarización alta.',items:['Apoyo gubernamental a PYMES y emprendimiento creativo.','Incertidumbre por posibles decretos fiscales.','Seguridad territorial afecta cadenas de suministro locales.']},
    e:{h3:'Económico',h4:'Reactivación del comercio y gasto en bienes personales.',items:['Crece el gasto de los hogares en artículos de autoexpresión.','Tasas de interés altas limitan el crédito para lujo.']},
    s:{h3:'Social',h4:'Joyería como vehículo de identidad.',items:['Auge del maximalismo y simbolismo personal.','Valor emocional por encima del transaccional.']},
    t:{h3:'Tecnológico',h4:'Digitalización y diseño asistido.',items:['Storytelling visual como motor de diferenciación.','Impresión 3D y software de diseño elevan precisión.']},
    ec:{h3:'Ecológico',h4:'Demanda por joyería ética y sostenible.',items:['Regulación creciente sobre residuos químicos.','Preferencia por metales trazables y packaging responsable.']},
    l:{h3:'Legal',h4:'Propiedad intelectual y normas ambientales.',items:['Protección de diseños originales.','Regulación de químicos y residuos peligrosos.']}
  };
  const d=data[type];
  document.getElementById('pestelH3').textContent=d.h3;
  document.getElementById('pestelH4').textContent=d.h4;
  document.getElementById('pestelList').innerHTML=d.items.map(i=>`<li>${i}</li>`).join('');
}

// BMC toggle
function toggleBmc(cell){
  const wasActive=cell.classList.contains('active');
  document.querySelectorAll('.bmc-cell').forEach(c=>c.classList.remove('active'));
  if(!wasActive) cell.classList.add('active');
}

// Modal
function openModal(type){
  const overlay=document.getElementById('modalOverlay');
  const content=document.getElementById('modalContent');
  const modals={
    awareness:`<h2>Awareness</h2>
      <p class="sub"><b>Objetivo:</b> Generar impacto masivo, atrayendo tráfico cualificado y validando nuestra propuesta de valor simbólica.</p>
      <div class="modal-section"><h3>Distribución de inversión · €15.000</h3>
        <div class="modal-bar"><div class="top"><span class="name">Paid Media (Meta + TikTok Ads)</span><span class="amount">€6.600</span></div><div class="sub">Reach + frecuencia</div><div class="track"><div class="fill" style="width:44%"></div></div></div>
        <div class="modal-bar"><div class="top"><span class="name">Influencer Marketing micro</span><span class="amount">€6.000</span></div><div class="sub">Storytelling auténtico</div><div class="track"><div class="fill" style="width:40%"></div></div></div>
        <div class="modal-bar"><div class="top"><span class="name">SEO + Contenido orgánico</span><span class="amount">€2.400</span></div><div class="sub">Autoridad y descubrimiento</div><div class="track"><div class="fill" style="width:16%"></div></div></div>
      </div>
      <div class="modal-section"><h3>Tácticas clave</h3>
        <div class="modal-tactics">
          <div class="modal-tactic"><div class="num">01</div><p>Cápsulas visuales "historia detrás del amuleto" (Reels / TikTok).</p></div>
          <div class="modal-tactic"><div class="num">02</div><p>Colaboraciones con micro-influencers (engagement >5%) en Bogotá. Se trata de colaboraciones gift y no colaboraciones remuneradas.</p></div>
          <div class="modal-tactic"><div class="num">03</div><p>Artículos SEO sobre simbolismo, materiales y rituales.</p></div>
          <div class="modal-tactic"><div class="num">04</div><p>Lanzamiento del manifiesto de marca.</p></div>
        </div>
      </div>
      <div class="modal-section"><h3>Funnels por canal</h3>
        <div class="modal-funnel"><h4>Funnel Paid Media</h4><div class="modal-funnel-row"><div class="modal-funnel-item"><div class="lb">Impresiones</div><div class="val">4.200.000</div></div><div class="modal-funnel-item"><div class="lb">Clicks</div><div class="val">63.000</div></div><div class="modal-funnel-item"><div class="lb">Seguidores</div><div class="val">10.584</div></div><div class="modal-funnel-item"><div class="lb">Leads</div><div class="val">106</div></div><div class="modal-funnel-item"><div class="lb">Conversiones</div><div class="val">2</div></div></div></div>
        <div class="modal-funnel"><h4>Funnel Influencer Marketing</h4><div class="modal-funnel-row"><div class="modal-funnel-item"><div class="lb">Impresiones</div><div class="val">1.800.000</div></div><div class="modal-funnel-item"><div class="lb">Clicks</div><div class="val">27.000</div></div><div class="modal-funnel-item"><div class="lb">Seguidores</div><div class="val">4.536</div></div><div class="modal-funnel-item"><div class="lb">Leads</div><div class="val">45</div></div><div class="modal-funnel-item"><div class="lb">Conversiones</div><div class="val">1</div></div></div></div>
        <div class="modal-funnel"><h4>Funnel SEO</h4><div class="modal-funnel-row"><div class="modal-funnel-item"><div class="lb">Impresiones</div><div class="val">1.200.000</div></div><div class="modal-funnel-item"><div class="lb">Clicks</div><div class="val">14.400</div></div><div class="modal-funnel-item"><div class="lb">Visitas</div><div class="val">11.520</div></div><div class="modal-funnel-item"><div class="lb">Leads</div><div class="val">46</div></div><div class="modal-funnel-item"><div class="lb">Conversiones</div><div class="val">1</div></div></div></div>
      </div>
      <div class="modal-section"><h3>KPIs proyectados</h3>
        <div class="modal-kpis">
          <div class="modal-kpi"><div class="lb">Impresiones totales</div><div class="val">7.200.000</div></div>
          <div class="modal-kpi"><div class="lb">Clicks calificados</div><div class="val">104.400</div></div>
          <div class="modal-kpi"><div class="lb">CPF total</div><div class="val">€0.99</div></div>
          <div class="modal-kpi"><div class="lb">Tasa de rebote total</div><div class="val">89%</div></div>
        </div>
      </div>`,
    captacion:`<h2>Captación</h2>
      <p class="sub"><b>Objetivo:</b> Convertir el alcance generado en leads cualificados con intención real de compra. Construir base propia (email + retargeting) y reducir dependencia algorítmica.</p>
      <div class="modal-section"><h3>Distribución de inversión · €35.000</h3>
        <div class="modal-bar"><div class="top"><span class="name">Email Marketing</span><span class="amount">€15.000</span></div><div class="sub">Lead nurturing</div><div class="track"><div class="fill" style="width:43%"></div></div></div>
        <div class="modal-bar"><div class="top"><span class="name">Campañas Instagram</span><span class="amount">€10.000</span></div><div class="sub">Captación masiva</div><div class="track"><div class="fill" style="width:29%"></div></div></div>
        <div class="modal-bar"><div class="top"><span class="name">Campañas TikTok</span><span class="amount">€5.000</span></div><div class="sub">Captación creativa</div><div class="track"><div class="fill" style="width:14%"></div></div></div>
        <div class="modal-bar"><div class="top"><span class="name">Marketing afiliación</span><span class="amount">€5.000</span></div><div class="sub">Recomendación</div><div class="track"><div class="fill" style="width:14%"></div></div></div>
      </div>
      <div class="modal-section"><h3>Tácticas clave</h3>
        <div class="modal-tactics">
          <div class="modal-tactic"><div class="num">01</div><p>Utilizaremos el email para convertir ese tráfico masivo en registros cualificados para nuestro embudo.</p></div>
          <div class="modal-tactic"><div class="num">02</div><p>Trabajaremos con influencers para promocionar el beneficio de suscripción. Configuraremos campañas de retargeting en TikTok e Instagram dirigidas a formularios para captar leads.</p></div>
          <div class="modal-tactic"><div class="num">03</div><p>Bienvenida automatizada en 4 emails con storytelling.</p></div>
          <div class="modal-tactic"><div class="num">04</div><p>Retargeting visual a visitantes del landing.</p></div>
        </div>
      </div>
      <div class="modal-section"><h3>Funnels por canal</h3>
        <div class="modal-funnel"><h4>Funnel general Captación</h4><div class="modal-funnel-row"><div class="modal-funnel-item"><div class="lb">Impresiones</div><div class="val">4.456.640</div></div><div class="modal-funnel-item"><div class="lb">Clicks</div><div class="val">116.416</div></div><div class="modal-funnel-item"><div class="lb">Leads</div><div class="val">10.000</div></div><div class="modal-funnel-item"><div class="lb">Conversiones</div><div class="val">241</div></div><div class="modal-funnel-item"><div class="lb">Ingresos</div><div class="val">€37.957</div></div></div></div>
      </div>
      <div class="modal-section"><h3>KPIs proyectados</h3>
        <div class="modal-kpis">
          <div class="modal-kpi"><div class="lb">CPL promedio</div><div class="val">€3.50</div></div>
          <div class="modal-kpi"><div class="lb">Conversión leads</div><div class="val">2.41%</div></div>
          <div class="modal-kpi"><div class="lb">CTR</div><div class="val">2.6%</div></div>
          <div class="modal-kpi"><div class="lb">Leads totales</div><div class="val">10.000</div></div>
          <div class="modal-kpi"><div class="lb">Ingresos fase</div><div class="val">€37.957</div></div>
        </div>
      </div>`,
    conversion:`<h2>Conversión</h2>
      <p class="sub"><b>Objetivo:</b> Cerrar ventas con flujos automatizados, recuperación de carrito y campañas con incentivos puntuales que mantengan la coherencia de marca.</p>
      <div class="modal-section"><h3>Distribución de inversión · €40.000</h3>
        <div class="modal-bar"><div class="top"><span class="name">Paid Media</span><span class="amount">€9.350</span></div><div class="sub">Lookalike + DPA</div><div class="track"><div class="fill" style="width:23%"></div></div></div>
        <div class="modal-bar"><div class="top"><span class="name">Email Marketing</span><span class="amount">€8.600</span></div><div class="sub">Flujo carrito + post-quiz</div><div class="track"><div class="fill" style="width:22%"></div></div></div>
        <div class="modal-bar"><div class="top"><span class="name">SEM</span><span class="amount">€6.050</span></div><div class="sub">Long-tail keywords</div><div class="track"><div class="fill" style="width:15%"></div></div></div>
        <div class="modal-bar"><div class="top"><span class="name">Marketing afiliación</span><span class="amount">€16.000</span></div><div class="sub">Comisión CPA</div><div class="track"><div class="fill" style="width:40%"></div></div></div>
      </div>
      <div class="modal-section"><h3>Tácticas clave</h3>
        <div class="modal-tactics">
          <div class="modal-tactic"><div class="num">01</div><p>Trabajaremos con micro-influencers bajo un modelo CPA. Pagaremos una comisión del 20% por las primeras 10 ventas y del 30% si superan esa cifra, además de entregarles producto físico.</p></div>
          <div class="modal-tactic"><div class="num">02</div><p>Ejecutaremos campañas de conversión en TikTok e Instagram Ads dirigidas a audiencias con alta intención de compra.</p></div>
          <div class="modal-tactic"><div class="num">03</div><p>Enviaremos recordatorios de incentivos, beneficios exclusivos y ofertas de última oportunidad para empujar la decisión de compra.</p></div>
          <div class="modal-tactic"><div class="num">04</div><p>Pujaremos por long-tail keywords en lugar de términos genéricos para maximizar el presupuesto.</p></div>
        </div>
      </div>
      <div class="modal-section"><h3>KPIs proyectados</h3>
        <div class="modal-kpis">
          <div class="modal-kpi"><div class="lb">CPA promedio</div><div class="val">€24.14</div></div>
          <div class="modal-kpi"><div class="lb">Ventas totales</div><div class="val">1.657</div></div>
          <div class="modal-kpi"><div class="lb">Ventas email</div><div class="val">864</div></div>
          <div class="modal-kpi"><div class="lb">Ingresos fase</div><div class="val">€260.977</div></div>
          <div class="modal-kpi"><div class="lb">ROI</div><div class="val">552%</div></div>
        </div>
      </div>`,
    fidelizacion:`<h2>Fidelización</h2>
      <p class="sub"><b>Objetivo:</b> Transformar a nuestros clientes iniciales en una comunidad activa que genere recompras y contenido para la marca.</p>
      <div class="modal-section"><h3>Distribución de inversión · €10.000</h3>
        <div class="modal-bar"><div class="top"><span class="name">Gestión Redes Sociales</span><span class="amount">€6.250</span></div><div class="sub">Comunidad y UGC</div><div class="track"><div class="fill" style="width:63%"></div></div></div>
        <div class="modal-bar"><div class="top"><span class="name">Email de Fidelización</span><span class="amount">€3.750</span></div><div class="sub">Recompras y preventas</div><div class="track"><div class="fill" style="width:37%"></div></div></div>
      </div>
      <div class="modal-section"><h3>Tácticas clave</h3>
        <div class="modal-tactics">
          <div class="modal-tactic"><div class="num">01</div><p>Invertiremos 2.000€ en colaboraciones con videntes y creadoras de contenido espiritual para reforzar el significado de las joyas como amuletos.</p></div>
          <div class="modal-tactic"><div class="num">02</div><p>Mantendremos el contacto mensual mediante newsletters, contenido sobre bienestar, simbología, preventas exclusivas y estrategias de viralidad y aumento del ticket medio.</p></div>
        </div>
      </div>
      <div class="modal-section"><h3>KPIs proyectados</h3>
        <div class="modal-kpis">
          <div class="modal-kpi"><div class="lb">Recompra</div><div class="val">25%</div></div>
          <div class="modal-kpi"><div class="lb">Conversiones</div><div class="val">501</div></div>
          <div class="modal-kpi"><div class="lb">Conversión email</div><div class="val">15%</div></div>
          <div class="modal-kpi"><div class="lb">Ingresos fase</div><div class="val">€79.320</div></div>
          <div class="modal-kpi"><div class="lb">ROI</div><div class="val">693%</div></div>
        </div>
      </div>`,
    detalle2026:`<h2>Detalle mensual 2026</h2>
      <table class="monthly-table">
        <thead><tr><th>Mes</th><th>Ingresos</th><th>Egresos</th><th>Utilidad</th><th>ROI</th></tr></thead>
        <tbody>
        <tr><td>Ene</td><td>€0</td><td>€14.430</td><td class="neg">€-14.430</td><td class="neg">-100.0%</td></tr>
        <tr><td>Feb</td><td>€0</td><td>€15.920</td><td class="neg">€-15.920</td><td class="neg">-100.0%</td></tr>
        <tr><td>Mar</td><td>€702</td><td>€14.740</td><td class="neg">€-14.038</td><td class="neg">-95.2%</td></tr>
        <tr><td>Abr</td><td>€3.465</td><td>€35.264</td><td class="neg">€-31.799</td><td class="neg">-90.2%</td></tr>
        <tr><td>May</td><td>€6.300</td><td>€18.736</td><td class="neg">€-12.436</td><td class="neg">-66.4%</td></tr>
        <tr><td>Jun</td><td>€8.033</td><td>€11.994</td><td class="neg">€-3.961</td><td class="neg">-33.0%</td></tr>
        <tr><td>Jul</td><td>€54.495</td><td>€49.494</td><td class="pos">€5.001</td><td class="pos">10.1%</td></tr>
        <tr><td>Ago</td><td>€48.038</td><td>€30.083</td><td class="pos">€17.955</td><td class="pos">59.7%</td></tr>
        <tr><td>Sep</td><td>€33.863</td><td>€32.124</td><td class="pos">€1.738</td><td class="pos">5.4%</td></tr>
        <tr><td>Oct</td><td>€61.057</td><td>€52.281</td><td class="pos">€8.776</td><td class="pos">16.8%</td></tr>
        <tr><td>Nov</td><td>€70.269</td><td>€47.249</td><td class="pos">€23.020</td><td class="pos">48.7%</td></tr>
        <tr><td>Dic</td><td>€92.738</td><td>€32.624</td><td class="pos">€60.114</td><td class="pos">184.3%</td></tr>
        <tr><td><b>Total</b></td><td><b>€378.957</b></td><td><b>€355.420</b></td><td><b class="pos">€23.537</b></td><td><b class="pos">6.62%</b></td></tr>
        </tbody>
      </table>`,
    tam2026:`<h2>Año 2026 · Desglose de mercado</h2>
      <div class="modal-section">
        <div class="modal-bar"><div class="top"><span class="name">TAM · Mercado total</span></div><div class="amount">€247.000.000</div><div class="sub">Consumo anual de joyería en Bogotá estimado en torno a 247 millones de euros.</div></div>
        <div class="modal-bar"><div class="top"><span class="name">SAM · Mercado objetivo</span></div><div class="amount">€209.000.000</div><div class="sub">1.159.200 piezas anuales: 579.600 mujeres que compran 2 veces al año. ~13% del TAM.</div></div>
        <div class="modal-bar"><div class="top"><span class="name">SOM · Mercado alcanzable</span></div><div class="amount">€378.957</div><div class="sub">2.500 piezas anuales, objetivo realista para los primeros 12 meses; proyección a 6.250 piezas (€947.393) en 24 meses.</div></div>
      </div>`
  };
  const copyModals={
    tam2027:modals.tam2026,tam2028:modals.tam2026
  };
  content.innerHTML=modals[type]||copyModals[type]||'<p>Contenido próximamente</p>';
  overlay.classList.add('show');
}

function closeModal(){
  document.getElementById('modalOverlay').classList.remove('show');
}

document.getElementById('modalOverlay').addEventListener('click',e=>{
  if(e.target===e.currentTarget) closeModal();
});

// Map
document.getElementById('mapBtn').addEventListener('click',()=>{
  document.getElementById('mapOverlay').classList.add('show');
});
function closeMap(){
  document.getElementById('mapOverlay').classList.remove('show');
}
document.getElementById('mapOverlay').addEventListener('click',e=>{
  if(e.target===e.currentTarget) closeMap();
});

// Bar tooltip
function showBarTooltip(el,year,units){
  const tt=document.getElementById('barTooltip');
  const rect=el.getBoundingClientRect();
  const container=el.closest('.bar-chart').getBoundingClientRect();
  tt.style.display='block';
  tt.style.left=(rect.left-container.left+rect.width/2-40)+'px';
  tt.style.top=(rect.top-container.top-50)+'px';
  document.getElementById('barTooltipYear').textContent=year;
  document.getElementById('barTooltipVal').textContent='Unidades: '+units;
}
function hideBarTooltip(){
  document.getElementById('barTooltip').style.display='none';
}

// Simulator
      </div>`,
    conversion:`<h2>Conversión</h2>
      <p class="sub"><b>Objetivo:</b> Cerrar ventas con flujos automatizados, recuperación de carrito y campañas con incentivos puntuales que mantengan la coherencia de marca.</p>
      <div class="modal-section"><h3>Distribución de inversión · €40.000</h3>
        <div class="modal-bar"><div class="top"><span class="name">Paid Media</span><span class="amount">€9.350</span></div><div class="sub">Lookalike + DPA</div><div class="track"><div class="fill" style="width:23%"></div></div></div>
        <div class="modal-bar"><div class="top"><span class="name">Email Marketing</span><span class="amount">€8.600</span></div><div class="sub">Flujo carrito + post-quiz</div><div class="track"><div class="fill" style="width:22%"></div></div></div>
        <div class="modal-bar"><div class="top"><span class="name">SEM</span><span class="amount">€6.050</span></div><div class="sub">Long-tail keywords</div><div class="track"><div class="fill" style="width:15%"></div></div></div>
        <div class="modal-bar"><div class="top"><span class="name">Marketing afiliación</span><span class="amount">€16.000</span></div><div class="sub">Comisión CPA</div><div class="track"><div class="fill" style="width:40%"></div></div></div>
      </div>
      <div class="modal-section"><h3>Tácticas clave</h3>
        <div class="modal-tactics">
          <div class="modal-tactic"><div class="num">01</div><p>Trabajaremos con micro-influencers bajo un modelo CPA. Pagaremos una comisión del 20% por las primeras 10 ventas y del 30% si superan esa cifra, además de entregarles producto físico.</p></div>
          <div class="modal-tactic"><div class="num">02</div><p>Ejecutaremos campañas de conversión en TikTok e Instagram Ads dirigidas a audiencias con alta intención de compra.</p></div>
          <div class="modal-tactic"><div class="num">03</div><p>Enviaremos recordatorios de incentivos, beneficios exclusivos y ofertas de última oportunidad para empujar la decisión de compra.</p></div>
          <div class="modal-tactic"><div class="num">04</div><p>Pujaremos por long-tail keywords en lugar de términos genéricos para maximizar el presupuesto.</p></div>
        </div>
      </div>
      <div class="modal-section"><h3>KPIs proyectados</h3>
        <div class="modal-kpis">
          <div class="modal-kpi"><div class="lb">CPA promedio</div><div class="val">€24.14</div></div>
          <div class="modal-kpi"><div class="lb">Ventas totales</div><div class="val">1.657</div></div>
          <div class="modal-kpi"><div class="lb">Ventas email</div><div class="val">864</div></div>
          <div class="modal-kpi"><div class="lb">Ingresos fase</div><div class="val">€260.977</div></div>
          <div class="modal-kpi"><div class="lb">ROI</div><div class="val">552%</div></div>
        </div>
      </div>`,
    fidelizacion:`<h2>Fidelización</h2>
      <p class="sub"><b>Objetivo:</b> Transformar a nuestros clientes iniciales en una comunidad activa que genere recompras y contenido para la marca.</p>
      <div class="modal-section"><h3>Distribución de inversión · €10.000</h3>
        <div class="modal-bar"><div class="top"><span class="name">Gestión Redes Sociales</span><span class="amount">€6.250</span></div><div class="sub">Comunidad y UGC</div><div class="track"><div class="fill" style="width:63%"></div></div></div>
        <div class="modal-bar"><div class="top"><span class="name">Email de Fidelización</span><span class="amount">€3.750</span></div><div class="sub">Recompras y preventas</div><div class="track"><div class="fill" style="width:37%"></div></div></div>
      </div>
      <div class="modal-section"><h3>Tácticas clave</h3>
        <div class="modal-tactics">
          <div class="modal-tactic"><div class="num">01</div><p>Invertiremos 2.000€ en colaboraciones con videntes y creadoras de contenido espiritual para reforzar el significado de las joyas como amuletos.</p></div>
          <div class="modal-tactic"><div class="num">02</div><p>Mantendremos el contacto mensual mediante newsletters, contenido sobre bienestar, simbología, preventas exclusivas y estrategias de viralidad y aumento del ticket medio.</p></div>
        </div>
      </div>
      <div class="modal-section"><h3>KPIs proyectados</h3>
        <div class="modal-kpis">
          <div class="modal-kpi"><div class="lb">Recompra</div><div class="val">25%</div></div>
          <div class="modal-kpi"><div class="lb">Conversiones</div><div class="val">501</div></div>
          <div class="modal-kpi"><div class="lb">Conversión email</div><div class="val">15%</div></div>
          <div class="modal-kpi"><div class="lb">Ingresos fase</div><div class="val">€79.320</div></div>
          <div class="modal-kpi"><div class="lb">ROI</div><div class="val">693%</div></div>
        </div>
      </div>`,
    detalle2026:`<h2>Detalle mensual 2026</h2>
      <table class="monthly-table">
        <thead><tr><th>Mes</th><th>Ingresos</th><th>Egresos</th><th>Utilidad</th><th>ROI</th></tr></thead>
        <tbody>
        <tr><td>Ene</td><td>€0</td><td>€14.430</td><td class="neg">€-14.430</td><td class="neg">-100.0%</td></tr>
        <tr><td>Feb</td><td>€0</td><td>€15.920</td><td class="neg">€-15.920</td><td class="neg">-100.0%</td></tr>
        <tr><td>Mar</td><td>€702</td><td>€14.740</td><td class="neg">€-14.038</td><td class="neg">-95.2%</td></tr>
        <tr><td>Abr</td><td>€3.465</td><td>€35.264</td><td class="neg">€-31.799</td><td class="neg">-90.2%</td></tr>
        <tr><td>May</td><td>€6.300</td><td>€18.736</td><td class="neg">€-12.436</td><td class="neg">-66.4%</td></tr>
        <tr><td>Jun</td><td>€8.033</td><td>€11.994</td><td class="neg">€-3.961</td><td class="neg">-33.0%</td></tr>
        <tr><td>Jul</td><td>€54.495</td><td>€49.494</td><td class="pos">€5.001</td><td class="pos">10.1%</td></tr>
        <tr><td>Ago</td><td>€48.038</td><td>€30.083</td><td class="pos">€17.955</td><td class="pos">59.7%</td></tr>
        <tr><td>Sep</td><td>€33.863</td><td>€32.124</td><td class="pos">€1.738</td><td class="pos">5.4%</td></tr>
        <tr><td>Oct</td><td>€61.057</td><td>€52.281</td><td class="pos">€8.776</td><td class="pos">16.8%</td></tr>
        <tr><td>Nov</td><td>€70.269</td><td>€47.249</td><td class="pos">€23.020</td><td class="pos">48.7%</td></tr>
        <tr><td>Dic</td><td>€92.738</td><td>€32.624</td><td class="pos">€60.114</td><td class="pos">184.3%</td></tr>
        <tr><td><b>Total</b></td><td><b>€378.957</b></td><td><b>€355.420</b></td><td><b class="pos">€23.537</b></td><td><b class="pos">6.62%</b></td></tr>
        </tbody>
      </table>`,
    tam2026:`<h2>Año 2026 · Desglose de mercado</h2>
      <div class="modal-section">
        <div class="modal-bar"><div class="top"><span class="name">TAM · Mercado total</span></div><div class="amount">€247.000.000</div><div class="sub">Consumo anual de joyería en Bogotá estimado en torno a 247 millones de euros.</div></div>
        <div class="modal-bar"><div class="top"><span class="name">SAM · Mercado objetivo</span></div><div class="amount">€209.000.000</div><div class="sub">1.159.200 piezas anuales: 579.600 mujeres que compran 2 veces al año. ~13% del TAM.</div></div>
        <div class="modal-bar"><div class="top"><span class="name">SOM · Mercado alcanzable</span></div><div class="amount">€378.957</div><div class="sub">2.500 piezas anuales, objetivo realista para los primeros 12 meses; proyección a 6.250 piezas (€947.393) en 24 meses.</div></div>
      </div>`
  };
  const copyModals={
    tam2027:modals.tam2026,tam2028:modals.tam2026
  };
  content.innerHTML=modals[type]||copyModals[type]||'<p>Contenido próximamente</p>';
  overlay.classList.add('show');
}

function closeModal(){
  document.getElementById('modalOverlay').classList.remove('show');
}

document.getElementById('modalOverlay').addEventListener('click',e=>{
  if(e.target===e.currentTarget) closeModal();
});

// Map
document.getElementById('mapBtn').addEventListener('click',()=>{
  document.getElementById('mapOverlay').classList.add('show');
});
function closeMap(){
  document.getElementById('mapOverlay').classList.remove('show');
}
document.getElementById('mapOverlay').addEventListener('click',e=>{
  if(e.target===e.currentTarget) closeMap();
});

// Bar tooltip
function showBarTooltip(el,year,units){
  const tt=document.getElementById('barTooltip');
  const rect=el.getBoundingClientRect();
  const container=el.closest('.bar-chart').getBoundingClientRect();
  tt.style.display='block';
  tt.style.left=(rect.left-container.left+rect.width/2-40)+'px';
  tt.style.top=(rect.top-container.top-50)+'px';
  document.getElementById('barTooltipYear').textContent=year;
  document.getElementById('barTooltipVal').textContent='Unidades: '+units;
}
function hideBarTooltip(){
  document.getElementById('barTooltip').style.display='none';
}

// Simulator
function setupRealSliderMarkers(){
  const sliders=[
    {id:'simUnits',real:2500,min:500,max:10000},
    {id:'simPrice',real:152,min:50,max:400},
    {id:'simCost',real:62,min:10,max:200}
  ];
  
  sliders.forEach(({id,real,min,max})=>{
    const input=document.getElementById(id);
    if(!input || input.closest('.sim-slider-wrap')) return;
    
    const wrap=document.createElement('div');
    wrap.className='sim-slider-wrap';
    wrap.style.setProperty('--real',((real-min)/(max-min)*100)+'%');
    input.parentNode.insertBefore(wrap,input);
    wrap.appendChild(input);
    
    const marker=document.createElement('span');
    marker.className='sim-real-marker';
    wrap.appendChild(marker);
  });
}

function updateSim(){
   const u=parseInt(document.getElementById('simUnits').value);
  const p=parseInt(document.getElementById('simPrice').value);
  const c=parseInt(document.getElementById('simCost').value);
  
  // Update slider progress
  document.getElementById('simUnits').style.setProperty('--progress',((u-500)/9500*100)+'%');
  document.getElementById('simPrice').style.setProperty('--progress',((p-50)/350*100)+'%');
  document.getElementById('simCost').style.setProperty('--progress',((c-10)/190*100)+'%');
  
  const ingresos=u*p;
  const costos=200370+c*u;
  const utilidad=ingresos-costos;
  const margen=ingresos>0?((utilidad/ingresos)*100):0;
  const be=Math.ceil(200370/(p-c));
  
  document.getElementById('simUnitsVal').textContent=u.toLocaleString('es-ES');
  document.getElementById('simPriceVal').textContent='€'+p;
  document.getElementById('simCostVal').textContent='€'+c;
  document.getElementById('simSumUnits').textContent=u.toLocaleString('es-ES');
  document.getElementById('simSumPrice').textContent='€'+p;
  document.getElementById('simSumCost').textContent='€'+c;
  document.getElementById('simIngresos').textContent='€'+ingresos.toLocaleString('es-ES');
  document.getElementById('simUtilidad').textContent='€'+utilidad.toLocaleString('es-ES');
  document.getElementById('simMargen').textContent=margen.toFixed(1)+'%';
  document.getElementById('simBE').textContent=(be>0?be.toLocaleString('es-ES'):'∞')+' u.';
}


function resetSim(){
  document.getElementById('simUnits').value=2500;
  document.getElementById('simPrice').value=152;
  document.getElementById('simCost').value=62;
  updateSim();
}

updateSim();

// Break Even Chart
function drawBreakEvenChart(){
  const container=document.getElementById('breakEvenChart');
  const w=900;
  const h=380;
  const pad={t:46,r:36,b:58,l:68};
  const cw=w-pad.l-pad.r;
  const ch=h-pad.t-pad.b;
  
  const fixedCosts=200370;
  const price=151.58;
  const variableCost=62.02;
  const beUnits=2237;
  const alloraUnits=2500;
  const maxUnits=5000;
  const maxVal=800000;
  
  function x(u){return pad.l+(u/maxUnits)*cw}
  function y(v){return pad.t+ch-(v/maxVal)*ch}
  
  let svg=`<svg class="chart-svg" viewBox="0 0 ${w} ${h}" xmlns="http://www.w3.org/2000/svg">`;
  // Grid
  for(let v=0;v<=maxVal;v+=200000){
    const yy=y(v);
    svg+=`<line x1="${pad.l}" y1="${yy}" x2="${w-pad.r}" y2="${yy}" stroke="rgba(92,184,155,.08)" stroke-width="1"/>`;
    svg+=`<text x="${pad.l-8}" y="${yy+4}" text-anchor="end" font-size="10" fill="#7a9a8e">${v/1000}k</text>`;
  }
  for(let u=0;u<=maxUnits;u+=500){
    const xx=x(u);
    svg+=`<line x1="${xx}" y1="${pad.t}" x2="${xx}" y2="${h-pad.b}" stroke="rgba(92,184,155,.08)" stroke-width="1"/>`;
    svg+=`<text x="${xx}" y="${h-pad.b+16}" text-anchor="middle" font-size="10" fill="#7a9a8e">${u}</text>`;
  }
  
  // Cost line (dashed)
  const costLine=[];
  for(let u=0;u<=maxUnits;u+=100){
    costLine.push(`${x(u)},${y(200370+62.02*u)}`);
  }
  svg+=`<polyline points="${costLine.join(' ')}" fill="none" stroke="#5cb89b" stroke-width="2" stroke-dasharray="6,4" opacity=".6"/>`;
  
  // Revenue line (solid)
  const revLine=[];
  for(let u=0;u<=maxUnits;u+=100){
    revLine.push(`${x(u)},${y(152*u)}`);
  }
  svg+=`<polyline points="${revLine.join(' ')}" fill="none" stroke="#2ecc71" stroke-width="2.5"/>`;
  
  // BE line
  const beX=x(beUnits);
  svg+=`<line x1="${beX}" y1="${pad.t}" x2="${beX}" y2="${h-pad.b}" stroke="var(--primary)" stroke-width="1.5" stroke-dasharray="4,4"/>`;
  svg+=`<circle cx="${beX}" cy="${y(200370+62.02*beUnits)}" r="6" fill="var(--primary)"/>`;
  svg+=`<text x="${beX}" y="${pad.t-10}" text-anchor="middle" font-size="10" fill="var(--primary)" font-weight="600">Allora real · 2.500 u.</text>`;
  
  // Legend
  svg+=`<circle cx="${pad.l+60}" cy="${h-12}" r="4" fill="#5cb89b" opacity=".6"/>`;
  svg+=`<text x="${pad.l+68}" y="${h-8}" font-size="10" fill="#7a9a8e">Costos</text>`;
  svg+=`<circle cx="${pad.l+120}" cy="${h-12}" r="4" fill="#2ecc71"/>`;
  svg+=`<text x="${pad.l+128}" y="${h-8}" font-size="10" fill="#7a9a8e">Ingresos</text>`;
  
  svg+=`</svg>`;
  container.innerHTML=svg;
}

drawBreakEvenChart();

// Projection Chart
function drawProjChart(){
  const container=document.getElementById('projChart');
  const w=container.clientWidth;
  const h=300;
  const pad={t:30,r:30,b:50,l:60};
  const cw=w-pad.l-pad.r;
  const ch=h-pad.t-pad.b;
  
  const years=[2026,2027,2028];
  const ingresos=[378957,947393,1610569];
  const utilidad=[23537,290573,579985];
  const maxVal=1800000;
  
  function x(i){return pad.l+(i/(years.length-1))*cw}
  function y(v){return pad.t+ch-(v/maxVal)*ch}
  
  let svg=`<svg class="chart-svg" viewBox="0 0 ${w} ${h}" xmlns="http://www.w3.org/2000/svg">`;
  // Grid
  for(let v=0;v<=maxVal;v+=450000){
    const yy=y(v);
    svg+=`<line x1="${pad.l}" y1="${yy}" x2="${w-pad.r}" y2="${yy}" stroke="rgba(92,184,155,.08)" stroke-width="1"/>`;
    svg+=`<text x="${pad.l-8}" y="${yy+4}" text-anchor="end" font-size="10" fill="#7a9a8e">${(v/1000).toFixed(0)}k</text>`;
  }
  years.forEach((yr,i)=>{
    const xx=x(i);
    svg+=`<text x="${xx}" y="${h-pad.b+16}" text-anchor="middle" font-size="10" fill="#7a9a8e">${yr}</text>`;
  });
  
  // Area fill for ingresos
  const areaPoints=years.map((_,i)=>`${x(i)},${y(ingresos[i])}`).join(' ')+' '+`${x(years.length-1)},${y(0)} ${x(0)},${y(0)}`;
  svg+=`<polygon points="${areaPoints}" fill="url(#areaGrad)" opacity=".3"/>`;
  svg+=`<defs><linearGradient id="areaGrad" x1="0" y1="0" x2="0" y2="1"><stop offset="0%" stop-color="#5cb89b" stop-opacity=".4"/><stop offset="100%" stop-color="#5cb89b" stop-opacity="0"/></linearGradient></defs>`;
  
  // Ingresos line
  const ingLine=years.map((_,i)=>`${x(i)},${y(ingresos[i])}`).join(' ');
  svg+=`<polyline points="${ingLine}" fill="none" stroke="#2ecc71" stroke-width="2.5"/>`;
  years.forEach((_,i)=>{
    svg+=`<circle cx="${x(i)}" cy="${y(ingresos[i])}" r="4" fill="#2ecc71"/>`;
  });
  
  // Utilidad line
  const utLine=years.map((_,i)=>`${x(i)},${y(utilidad[i])}`).join(' ');
  svg+=`<polyline points="${utLine}" fill="none" stroke="#5cb89b" stroke-width="2" stroke-dasharray="5,3"/>`;
  years.forEach((_,i)=>{
    svg+=`<circle cx="${x(i)}" cy="${y(utilidad[i])}" r="3" fill="#5cb89b"/>`;
  });
  
  // Legend
  svg+=`<circle cx="${pad.l+40}" cy="${h-12}" r="4" fill="#2ecc71"/>`;
  svg+=`<text x="${pad.l+48}" y="${h-8}" font-size="10" fill="#7a9a8e">Ingresos</text>`;
  svg+=`<circle cx="${pad.l+100}" cy="${h-12}" r="3" fill="#5cb89b"/>`;
  svg+=`<text x="${pad.l+108}" y="${h-8}" font-size="10" fill="#7a9a8e">Utilidad</text>`;
  
  svg+=`</svg>`;
  container.innerHTML=svg;
}

drawProjChart();

// P&L Chart
function drawPLChart(){
  const container=document.getElementById('plChart');
  const w=container.clientWidth;
  const h=350;
  const pad={t:30,r:30,b:50,l:60};
  const cw=w-pad.l-pad.r;
  const ch=h-pad.t-pad.b;
  
  const meses=['Ene','Feb','Mar','Abr','May','Jun','Jul','Ago','Sep','Oct','Nov','Dic'];
  const ingresos=[0,0,702,3465,6300,8033,54495,48038,33863,61057,70269,92738];
  const egresos=[14430,15920,14740,35264,18736,11994,49494,30083,32124,52281,47249,32624];
  const utilidad=ingresos.map((ing,i)=>ing-egresos[i]);
  const maxVal=105000;
  const minVal=-35000;
  const range=maxVal-minVal;
  
  function x(i){return pad.l+(i/(meses.length-1))*cw}
  function y(v){return pad.t+ch-((v-minVal)/range)*ch}
  
  let svg=`<svg class="chart-svg" viewBox="0 0 ${w} ${h}" xmlns="http://www.w3.org/2000/svg">`;
  // Zero line
  const zeroY=y(0);
  svg+=`<line x1="${pad.l}" y1="${zeroY}" x2="${w-pad.r}" y2="${zeroY}" stroke="rgba(92,184,155,.15)" stroke-width="1"/>`;
  
  // Grid
  for(let v=-35000;v<=105000;v+=35000){
    const yy=y(v);
    svg+=`<line x1="${pad.l}" y1="${yy}" x2="${w-pad.r}" y2="${yy}" stroke="rgba(92,184,155,.06)" stroke-width="1"/>`;
    svg+=`<text x="${pad.l-8}" y="${yy+4}" text-anchor="end" font-size="10" fill="#7a9a8e">${v>=0?(v/1000)+'k':'-'+(-v/1000)+'k'}</text>`;
  }
  
  // Bars
  const barW=cw/meses.length*0.5;
  meses.forEach((m,i)=>{
    const xx=x(i)-barW/2;
    // Ingresos bar
    const ingH=Math.max(0,(ingresos[i]/maxVal)*ch*0.6);
    svg+=`<rect x="${xx}" y="${zeroY-ingH}" width="${barW*0.45}" height="${ingH}" fill="#5cb89b" opacity=".5" rx="3"/>`;
    // Egresos bar
    const egH=Math.max(0,(egresos[i]/maxVal)*ch*0.6);
    svg+=`<rect x="${xx+barW*0.5}" y="${zeroY-egH}" width="${barW*0.45}" height="${egH}" fill="#5cb89b" opacity=".3" rx="3"/>`;
    svg+=`<text x="${x(i)}" y="${h-pad.b+16}" text-anchor="middle" font-size="10" fill="#7a9a8e">${m}</text>`;
  });
  
  // Utilidad line
  const utLine=meses.map((_,i)=>`${x(i)},${y(utilidad[i])}`).join(' ');
  svg+=`<polyline points="${utLine}" fill="none" stroke="#2ecc71" stroke-width="2"/>`;
  meses.forEach((_,i)=>{
    svg+=`<circle cx="${x(i)}" cy="${y(utilidad[i])}" r="3" fill="#2ecc71"/>`;
  });
  
  // Legend
  svg+=`<circle cx="${pad.l+40}" cy="${h-12}" r="4" fill="#5cb89b" opacity=".5"/>`;
  svg+=`<text x="${pad.l+48}" y="${h-8}" font-size="10" fill="#7a9a8e">Ingresos</text>`;
  svg+=`<circle cx="${pad.l+110}" cy="${h-12}" r="4" fill="#5cb89b" opacity=".3"/>`;
  svg+=`<text x="${pad.l+118}" y="${h-8}" font-size="10" fill="#7a9a8e">Egresos</text>`;
  svg+=`<circle cx="${pad.l+180}" cy="${h-12}" r="3" fill="#2ecc71"/>`;
  svg+=`<text x="${pad.l+188}" y="${h-8}" font-size="10" fill="#7a9a8e">Utilidad</text>`;
  
  svg+=`</svg>`;
  container.innerHTML=svg;
}

drawPLChart();
  
  function toggleLC(card){
  card.classList.toggle('open');
}


// Resize charts
window.addEventListener('resize',()=>{
  drawBreakEvenChart();
  drawProjChart();
  drawPLChart();
});

// Smooth scroll for nav links
document.querySelectorAll('a[href^="#"]').forEach(a=>{
  a.addEventListener('click',e=>{
    const id=a.getAttribute('href');
    if(id==='#') return;
    const el=document.querySelector(id);
    if(el){
      e.preventDefault();
      const y=el.getBoundingClientRect().top+window.pageYOffset-100;
      window.scrollTo({top:y,behavior:'smooth'});
      closeAllDd();
    }
  });
});
</script>
</body>
</html>

