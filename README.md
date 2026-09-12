<!DOCTYPE html>
<html lang="vi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Học sinh an toàn trên không gian mạng</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Be+Vietnam+Pro:wght@400;500;600;700;800&display=swap" rel="stylesheet">
<style>
  :root{
    --navy:#1B2140;
    --indigo:#3652C4;
    --indigo-light:#EEF1FC;
    --mint:#1F9D77;
    --mint-light:#E5F7F0;
    --coral:#E6543F;
    --coral-light:#FDEAE7;
    --amber:#C77A00;
    --amber-light:#FDF1DD;
    --bg:#F6F7FB;
    --surface:#FFFFFF;
    --line:#E2E5F0;
    --ink:#1B2140;
    --ink-soft:#565C7A;
    --radius:18px;
  }
  *{box-sizing:border-box;}
  html,body{margin:0;padding:0;}
  body{
    font-family:'Be Vietnam Pro', sans-serif;
    background:var(--bg);
    color:var(--ink);
    -webkit-font-smoothing:antialiased;
  }
  @media (prefers-reduced-motion: reduce){
    *{animation:none !important; transition:none !important;}
  }
  .app{
    max-width:480px;
    margin:0 auto;
    min-height:100vh;
    background:var(--bg);
    display:flex;
    flex-direction:column;
    position:relative;
  }
  /* ---- Top bar ---- */
  .topbar{
    background:var(--navy);
    color:#fff;
    padding:18px 20px 20px;
    display:flex;
    align-items:center;
    gap:12px;
  }
  .topbar .mark{
    width:40px;height:40px;flex:none;
  }
  .topbar h1{
    font-size:16px;
    line-height:1.3;
    margin:0;
    font-weight:700;
    letter-spacing:.1px;
  }
  .topbar p{
    margin:2px 0 0;
    font-size:12.5px;
    color:#B7BEE8;
  }
  /* ---- Pages ---- */
  main{
    flex:1;
    padding:22px 18px 100px;
  }
  .page{display:none;}
  .page.active{display:block; animation:rise .35s ease;}
  @keyframes rise{from{opacity:0; transform:translateY(8px);} to{opacity:1; transform:none;}}

  h2.page-title{
    font-size:23px;
    font-weight:800;
    margin:0 0 6px;
    line-height:1.25;
  }
  .page-lede{
    color:var(--ink-soft);
    font-size:14.5px;
    line-height:1.55;
    margin:0 0 22px;
  }
  .card{
    background:var(--surface);
    border:1px solid var(--line);
    border-radius:var(--radius);
    padding:18px;
    margin-bottom:14px;
  }
  .card h3{
    font-size:15.5px;
    margin:0 0 6px;
    font-weight:700;
  }
  .card p{
    font-size:13.8px;
    color:var(--ink-soft);
    line-height:1.55;
    margin:0;
  }
  .tip-list{list-style:none; margin:0; padding:0;}
  .tip-list li{
    display:flex; gap:10px;
    font-size:14px; line-height:1.5;
    color:var(--ink);
    padding:9px 0;
    border-bottom:1px solid var(--line);
  }
  .tip-list li:last-child{border-bottom:none;}
  .tip-list .ico{flex:none; font-size:16px; margin-top:1px;}

  .badge{
    display:inline-flex; align-items:center; gap:6px;
    font-size:12px; font-weight:700;
    padding:4px 10px; border-radius:100px;
  }
  .badge.safe{background:var(--mint-light); color:var(--mint);}
  .badge.danger{background:var(--coral-light); color:var(--coral);}
  .badge.warn{background:var(--amber-light); color:var(--amber);}

  /* ---- Home ---- */
  .hero{
    background:var(--navy);
    margin:-22px -18px 22px;
    padding:26px 20px 30px;
    color:#fff;
    border-radius:0 0 26px 26px;
  }
  .hero h2{
    font-size:24px;
    line-height:1.3;
    font-weight:800;
    margin:16px 0 8px;
  }
  .hero p{
    font-size:13.8px;
    color:#C4CAEE;
    line-height:1.55;
    margin:0 0 18px;
    max-width:38ch;
  }
  .hero-actions{display:flex; gap:10px; flex-wrap:wrap;}
  .btn{
    border:none; cursor:pointer;
    font-family:inherit;
    font-weight:700; font-size:13.5px;
    padding:11px 16px;
    border-radius:12px;
    display:inline-flex; align-items:center; gap:6px;
  }
  .btn.primary{background:#fff; color:var(--navy);}
  .btn.ghost{background:rgba(255,255,255,.12); color:#fff; border:1px solid rgba(255,255,255,.35);}
  .btn.block{width:100%; justify-content:center; margin-top:8px;}
  .btn.primary.solid{background:var(--indigo); color:#fff;}
  .btn:focus-visible{outline:3px solid #7C8FFF; outline-offset:2px;}

  .quick-grid{
    display:grid; grid-template-columns:1fr 1fr; gap:10px;
    margin-top:4px;
  }
  .quick-tile{
    background:var(--surface); border:1px solid var(--line);
    border-radius:14px; padding:14px;
    text-align:left; cursor:pointer; font-family:inherit;
    display:flex; flex-direction:column; gap:8px;
  }
  .quick-tile:focus-visible{outline:3px solid var(--indigo); outline-offset:2px;}
  .quick-tile .qi{font-size:20px;}
  .quick-tile b{font-size:13.5px;}
  .quick-tile span{font-size:11.5px; color:var(--ink-soft); line-height:1.4;}

  .section-label{
    font-size:12px; font-weight:700; color:var(--ink-soft);
    margin:26px 0 10px;
  }

  /* ---- Scenario cards (phishing) ---- */
  .scenario{
    border-radius:var(--radius);
    padding:16px;
    margin-bottom:12px;
    border:1px solid var(--line);
  }
  .scenario.bad{background:var(--coral-light); border-color:#F3CFC8;}
  .scenario.good{background:var(--mint-light); border-color:#C6E9DB;}
  .scenario .msg{
    background:var(--surface);
    border-radius:10px;
    padding:11px 12px;
    font-size:13.3px;
    line-height:1.5;
    margin:8px 0 10px;
    color:var(--ink);
  }
  .scenario .why{font-size:12.8px; color:var(--ink-soft); line-height:1.5;}

  /* ---- Password checker ---- */
  .pw-box input{
    width:100%; padding:12px 14px;
    border-radius:12px; border:1.5px solid var(--line);
    font-size:15px; font-family:inherit;
    margin-bottom:10px;
  }
  .pw-box input:focus-visible{outline:3px solid var(--indigo); outline-offset:1px; border-color:var(--indigo);}
  .meter{
    height:8px; background:var(--line); border-radius:100px; overflow:hidden; margin-bottom:8px;
  }
  .meter-fill{height:100%; width:0%; border-radius:100px; background:var(--coral); transition:width .25s ease, background .25s ease;}
  .meter-label{font-size:13px; font-weight:700;}
  .meter-hints{font-size:12px; color:var(--ink-soft); margin-top:6px; line-height:1.5;}

  /* ---- Quiz ---- */
  .q-progress{
    font-size:12.5px; color:var(--ink-soft); font-weight:600; margin-bottom:6px;
  }
  .q-track{height:6px; background:var(--line); border-radius:100px; margin-bottom:22px; overflow:hidden;}
  .q-track-fill{height:100%; background:var(--indigo); border-radius:100px; transition:width .3s ease;}
  .q-card{background:var(--surface); border:1px solid var(--line); border-radius:var(--radius); padding:18px;}
  .q-text{font-size:15.5px; font-weight:700; line-height:1.45; margin:0 0 14px;}
  .q-opt{
    display:block; width:100%; text-align:left;
    background:var(--bg); border:1.5px solid var(--line);
    border-radius:12px; padding:12px 14px; margin-bottom:9px;
    font-family:inherit; font-size:13.8px; color:var(--ink);
    cursor:pointer;
  }
  .q-opt:focus-visible{outline:3px solid var(--indigo); outline-offset:2px;}
  .q-opt.correct{background:var(--mint-light); border-color:var(--mint); color:#0F5C43; font-weight:700;}
  .q-opt.incorrect{background:var(--coral-light); border-color:var(--coral); color:#8E2E1F; font-weight:700;}
  .q-opt[disabled]{cursor:default;}
  .q-explain{
    font-size:13px; color:var(--ink-soft); line-height:1.5;
    background:var(--indigo-light); border-radius:10px; padding:11px 12px; margin-top:6px;
    display:none;
  }
  .q-explain.show{display:block;}
  .q-nav{display:flex; justify-content:flex-end; margin-top:16px;}
  .q-result{text-align:center; padding:10px 4px 4px;}
  .q-result .score{font-size:42px; font-weight:800; color:var(--indigo); margin:6px 0 2px;}
  .q-result .score span{font-size:20px; color:var(--ink-soft); font-weight:600;}
  .q-result p{color:var(--ink-soft); font-size:14px; margin:6px 0 18px;}

  /* ---- Bottom tab bar ---- */
  .tabbar{
    position:sticky; bottom:0; left:0; right:0;
    background:var(--surface);
    border-top:1px solid var(--line);
    display:flex;
    padding:6px 4px calc(6px + env(safe-area-inset-bottom));
    max-width:480px;
    margin:0 auto;
    width:100%;
  }
  .tab{
    flex:1; background:none; border:none; font-family:inherit;
    display:flex; flex-direction:column; align-items:center; gap:3px;
    padding:8px 2px; cursor:pointer; color:var(--ink-soft);
    border-radius:10px;
  }
  .tab .ti{font-size:19px;}
  .tab .tl{font-size:10px; font-weight:600;}
  .tab.active{color:var(--indigo);}
  .tab:focus-visible{outline:2px solid var(--indigo); outline-offset:-2px;}
</style>
</head>
<body>
<div class="app">

  <header class="topbar">
    <svg class="mark" viewBox="0 0 40 40" fill="none">
      <path d="M20 3 L34 8 V19 C34 28 28 34 20 37 C12 34 6 28 6 19 V8 Z" fill="#3652C4"/>
      <path d="M20 3 L34 8 V19 C34 28 28 34 20 37 V3Z" fill="#4E68DB"/>
      <circle cx="20" cy="18" r="5.5" fill="#fff"/>
      <rect x="17" y="18" width="6" height="7" rx="1.5" fill="#fff"/>
    </svg>
    <div>
      <h1>Học sinh an toàn trên<br>không gian mạng</h1>
      <p>Kiến thức an toàn mạng cho học sinh</p>
    </div>
  </header>

  <main id="pages">

    <!-- ======================= TRANG CHỦ ======================= -->
    <section class="page active" id="page-home">
      <div class="hero">
        <span class="badge warn" style="background:rgba(255,255,255,.15); color:#FFD98C;">5 phút mỗi ngày</span>
        <h2>Lên mạng an toàn,<br>không lo bị lừa</h2>
        <p>Một chiếc điện thoại có thể mở ra cả thế giới — nhưng cũng có thể là nơi kẻ xấu tìm cách lừa bạn. Trang này giúp bạn nhận biết và tự bảo vệ mình.</p>
        <div class="hero-actions">
          <button class="btn primary" data-nav="password">Bắt đầu học →</button>
          <button class="btn ghost" data-nav="quiz">Làm trắc nghiệm</button>
        </div>
      </div>

      <p class="page-lede" style="margin-bottom:16px;">Chỉ với vài thói quen nhỏ, bạn có thể tránh được phần lớn rủi ro thường gặp trên mạng. Chọn một chủ đề để bắt đầu:</p>

      <div class="quick-grid">
        <button class="quick-tile" data-nav="password">
          <span class="qi">🔑</span>
          <b>Mật khẩu an toàn</b>
          <span>Tạo và bảo vệ mật khẩu đúng cách</span>
        </button>
        <button class="quick-tile" data-nav="phishing">
          <span class="qi">🔗</span>
          <b>Nhận diện lừa đảo</b>
          <span>Phát hiện link, tin nhắn giả mạo</span>
        </button>
        <button class="quick-tile" data-nav="privacy">
          <span class="qi">🛡️</span>
          <b>Thông tin cá nhân</b>
          <span>Biết điều gì nên và không nên chia sẻ</span>
        </button>
        <button class="quick-tile" data-nav="help">
          <span class="qi">🆘</span>
          <b>Khi gặp rắc rối</b>
          <span>Bị bắt nạt hoặc lừa đảo phải làm sao</span>
        </button>
      </div>

      <p class="section-label">VÌ SAO ĐIỀU NÀY QUAN TRỌNG</p>
      <div class="card">
        <p>Rất nhiều vụ mất tài khoản, lộ thông tin hay bị bắt nạt trên mạng bắt đầu từ những điều rất nhỏ: một mật khẩu dễ đoán, một đường link tò mò bấm thử, hoặc một tin nhắn tưởng chừng vô hại. Biết trước các dấu hiệu giúp bạn tránh được phần lớn rắc rối.</p>
      </div>
    </section>

    <!-- ======================= MẬT KHẨU ======================= -->
    <section class="page" id="page-password">
      <h2 class="page-title">Mật khẩu an toàn</h2>
      <p class="page-lede">Mật khẩu là lớp bảo vệ đầu tiên cho tài khoản của bạn. Một mật khẩu yếu cũng giống như khoá cửa nhà bằng một sợi dây thun.</p>

      <div class="card pw-box">
        <h3>Thử độ mạnh mật khẩu</h3>
        <p style="margin-bottom:10px;">Nhập thử một mật khẩu để xem mức độ an toàn (không lưu lại):</p>
        <input id="pwInput" type="text" placeholder="Nhập mật khẩu để kiểm tra..." autocomplete="off">
        <div class="meter"><div class="meter-fill" id="pwFill"></div></div>
        <div class="meter-label" id="pwLabel" style="color:var(--ink-soft);">Chưa nhập mật khẩu</div>
        <div class="meter-hints" id="pwHints"></div>
      </div>

      <p class="section-label">CÁCH TẠO MẬT KHẨU TỐT</p>
      <div class="card">
        <ul class="tip-list">
          <li><span class="ico">✅</span> Dài ít nhất 8–12 ký tự, càng dài càng khó bị đoán ra.</li>
          <li><span class="ico">✅</span> Kết hợp chữ hoa, chữ thường, số và ký tự đặc biệt (@, #, !, $...).</li>
          <li><span class="ico">✅</span> Dùng một câu dễ nhớ với bạn rồi biến tấu, ví dụ: "Meo7Thich@AnCa" thay vì "meothichanca".</li>
          <li><span class="ico">✅</span> Bật xác thực 2 bước (2FA) cho các tài khoản quan trọng như Facebook, Gmail.</li>
          <li><span class="ico">✅</span> Dùng mật khẩu khác nhau cho từng tài khoản quan trọng.</li>
        </ul>
      </div>

      <p class="section-label">NHỮNG ĐIỀU NÊN TRÁNH</p>
      <div class="card">
        <ul class="tip-list">
          <li><span class="ico">🚫</span> Không dùng ngày sinh, tên, số điện thoại làm mật khẩu.</li>
          <li><span class="ico">🚫</span> Không dùng "123456", "password" hay các mật khẩu quá phổ biến.</li>
          <li><span class="ico">🚫</span> Không dùng chung một mật khẩu cho nhiều tài khoản.</li>
          <li><span class="ico">🚫</span> Không nói mật khẩu cho bạn bè, kể cả bạn thân.</li>
          <li><span class="ico">🚫</span> Không lưu mật khẩu ở nơi người khác dễ thấy (ghi giấy dán màn hình...).</li>
        </ul>
      </div>
    </section>

    <!-- ======================= LỪA ĐẢO ======================= -->
    <section class="page" id="page-phishing">
      <h2 class="page-title">Nhận diện lừa đảo</h2>
      <p class="page-lede">Tin nhắn và đường link lừa đảo thường có chung một vài dấu hiệu. So sánh hai ví dụ dưới đây:</p>

      <div class="scenario bad">
        <span class="badge danger">⚠ Đáng ngờ</span>
        <div class="msg">"Chúc mừng bạn đã trúng thưởng điện thoại iPhone! Bấm vào link sau và nhập mật khẩu Facebook để nhận thưởng ngay hôm nay: bit.ly/nhanqua-gap"</div>
        <div class="why">Tạo cảm giác gấp gáp, hứa hẹn phần thưởng lớn bất ngờ, yêu cầu mật khẩu, dùng link rút gọn lạ.</div>
      </div>

      <div class="scenario good">
        <span class="badge safe">✓ Bình thường</span>
        <div class="msg">"Cô Lan đây, mai lớp mình kiểm tra 15 phút môn Sử nhé, các em nhớ ôn bài chương 3."</div>
        <div class="why">Người gửi rõ ràng, nội dung hợp lý, không yêu cầu bấm link hay cung cấp thông tin.</div>
      </div>

      <p class="section-label">5 DẤU HIỆU CẦN CẢNH GIÁC</p>
      <div class="card">
        <ul class="tip-list">
          <li><span class="ico">1️⃣</span> Thúc giục bạn hành động thật nhanh ("chỉ còn hôm nay", "gấp"...).</li>
          <li><span class="ico">2️⃣</span> Hứa hẹn phần thưởng lớn mà bạn không hề tham gia.</li>
          <li><span class="ico">3️⃣</span> Yêu cầu mật khẩu, mã OTP hoặc thông tin thẻ ngân hàng.</li>
          <li><span class="ico">4️⃣</span> Đường link lạ, viết sai chính tả tên thương hiệu (vd: "faceb00k.com").</li>
          <li><span class="ico">5️⃣</span> Người gửi lạ, hoặc tài khoản quen nhưng nhắn tin khác lạ thường ngày.</li>
        </ul>
      </div>

      <p class="section-label">NÊN LÀM GÌ</p>
      <div class="card">
        <p>Không bấm vào link lạ. Không nhập mật khẩu hay mã OTP vào trang không rõ nguồn gốc. Nếu nghi ngờ, hãy hỏi lại người gửi bằng cách khác (gọi điện) hoặc hỏi người lớn trước khi làm theo.</p>
      </div>
    </section>

    <!-- ======================= THÔNG TIN CÁ NHÂN ======================= -->
    <section class="page" id="page-privacy">
      <h2 class="page-title">Bảo vệ thông tin cá nhân</h2>
      <p class="page-lede">Mỗi thông tin bạn đăng lên mạng đều có thể bị người lạ thu thập và sử dụng sai mục đích.</p>

      <p class="section-label">HẠN CHẾ CHIA SẺ CÔNG KHAI</p>
      <div class="card">
        <ul class="tip-list">
          <li><span class="ico">🏠</span> Địa chỉ nhà, số điện thoại cá nhân.</li>
          <li><span class="ico">🏫</span> Tên trường, lớp học và lịch học/lịch di chuyển hằng ngày.</li>
          <li><span class="ico">📍</span> Vị trí hiện tại (bật định vị khi đăng ảnh).</li>
          <li><span class="ico">💳</span> Thông tin tài khoản ngân hàng, mã OTP.</li>
          <li><span class="ico">🪪</span> Ảnh giấy tờ tuỳ thân, thẻ học sinh.</li>
        </ul>
      </div>

      <p class="section-label">THÓI QUEN NÊN CÓ</p>
      <div class="card">
        <ul class="tip-list">
          <li><span class="ico">✅</span> Đặt chế độ riêng tư (Private) cho trang cá nhân, chỉ bạn bè xem được.</li>
          <li><span class="ico">✅</span> Cân nhắc kỹ trước khi chấp nhận kết bạn với người lạ.</li>
          <li><span class="ico">✅</span> Không cung cấp thông tin cá nhân để đổi lấy quà tặng, ưu đãi.</li>
          <li><span class="ico">✅</span> Hỏi ý kiến bố mẹ/thầy cô trước khi đăng ảnh có địa điểm cụ thể.</li>
        </ul>
      </div>

      <div class="card" style="background:var(--indigo-light); border-color:#D3DAF6;">
        <h3>Mẹo nhớ nhanh</h3>
        <p>Trước khi đăng hoặc gửi bất cứ điều gì, tự hỏi: "Nếu người lạ nhìn thấy điều này, mình có thoải mái không?". Nếu câu trả lời là không, đừng đăng.</p>
      </div>
    </section>

    <!-- ======================= XỬ LÝ SỰ CỐ ======================= -->
    <section class="page" id="page-help">
      <h2 class="page-title">Khi gặp rắc rối trên mạng</h2>
      <p class="page-lede">Nếu bị bắt nạt, đe doạ hoặc nghi ngờ đã bị lừa đảo, hãy bình tĩnh làm theo các bước sau.</p>

      <div class="card">
        <h3>😠 Nếu bị bắt nạt / đe doạ trên mạng</h3>
        <ul class="tip-list">
          <li><span class="ico">1</span> Không trả lời hay "cãi nhau" với người đó.</li>
          <li><span class="ico">2</span> Chụp lại màn hình làm bằng chứng.</li>
          <li><span class="ico">3</span> Chặn (block) và báo cáo (report) tài khoản đó.</li>
          <li><span class="ico">4</span> Kể ngay cho bố mẹ, thầy cô hoặc người lớn tin cậy.</li>
        </ul>
      </div>

      <div class="card">
        <h3>🎣 Nếu nghi ngờ đã bị lừa đảo</h3>
        <ul class="tip-list">
          <li><span class="ico">1</span> Đổi mật khẩu ngay lập tức cho tài khoản liên quan.</li>
          <li><span class="ico">2</span> Không thực hiện thêm bất kỳ yêu cầu chuyển tiền/thông tin nào.</li>
          <li><span class="ico">3</span> Báo cho bố mẹ hoặc thầy cô để được hỗ trợ kịp thời.</li>
          <li><span class="ico">4</span> Báo cáo tài khoản/tin nhắn lừa đảo trên nền tảng đang dùng.</li>
        </ul>
      </div>

      <div class="card" style="background:var(--mint-light); border-color:#C6E9DB;">
        <h3>📞 Cần hỗ trợ ngay?</h3>
        <p>Tổng đài điện thoại Quốc gia Bảo vệ Trẻ em: <strong>111</strong> — miễn phí, hoạt động 24/7. Ngoài ra, luôn có thể tìm đến bố mẹ, thầy cô hoặc cán bộ tư vấn tâm lý của trường.</p>
      </div>

      <div class="card" style="background:var(--indigo-light); border-color:#D3DAF6;">
        <p><strong>Ghi nhớ:</strong> Không phải lỗi của bạn khi bị lừa hay bị bắt nạt. Nói ra với người lớn tin cậy luôn là bước đúng đắn nhất.</p>
      </div>
    </section>

    <!-- ======================= TRẮC NGHIỆM ======================= -->
    <section class="page" id="page-quiz">
      <h2 class="page-title">Trắc nghiệm kiến thức</h2>
      <p class="page-lede" id="quizIntro">10 câu hỏi giúp bạn kiểm tra lại những gì đã học. Chọn một đáp án cho mỗi câu.</p>

      <div id="quizArea"></div>
    </section>

  </main>

  <nav class="tabbar">
    <button class="tab active" data-nav="home"><span class="ti">🏠</span><span class="tl">Trang chủ</span></button>
    <button class="tab" data-nav="password"><span class="ti">🔑</span><span class="tl">Mật khẩu</span></button>
    <button class="tab" data-nav="phishing"><span class="ti">🔗</span><span class="tl">Lừa đảo</span></button>
    <button class="tab" data-nav="privacy"><span class="ti">🛡️</span><span class="tl">Cá nhân</span></bu
