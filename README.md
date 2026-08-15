# emr2
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="theme-color" content="#0b5cff">
<title>翔・Personal Medical Record</title>
<style>
:root{
  --blue:#0b5cff; --blue2:#48a9ff; --navy:#07152f; --ink:#10213f;
  --pale:#eef7ff; --card:rgba(255,255,255,.92); --line:#cfe4ff;
  --danger:#e5484d; --shadow:0 18px 45px rgba(7,45,105,.13);
}
*{box-sizing:border-box}
html{scroll-behavior:smooth}
body{
  margin:0; font-family:Inter,ui-sans-serif,system-ui,-apple-system,BlinkMacSystemFont,"Segoe UI",
  "Noto Sans TC","Noto Sans KR","Noto Sans JP",sans-serif; color:var(--ink);
  background:
    radial-gradient(circle at 8% 5%,rgba(72,169,255,.28),transparent 27%),
    radial-gradient(circle at 90% 15%,rgba(11,92,255,.18),transparent 25%),
    linear-gradient(145deg,#f8fcff,#e8f4ff 55%,#f7fbff);
  min-height:100vh;
}
body:before{
  content:"";position:fixed;inset:0;pointer-events:none;opacity:.055;
  background-image:linear-gradient(135deg,#0b5cff 1px,transparent 1px);
  background-size:34px 34px;
}
header{
  position:sticky;top:0;z-index:10;background:rgba(7,21,47,.94);
  backdrop-filter:blur(18px);color:white;border-bottom:1px solid rgba(255,255,255,.12)
}
.nav{max-width:1180px;margin:auto;padding:13px 20px;display:flex;gap:18px;align-items:center;justify-content:space-between}
.brand{display:flex;align-items:center;gap:11px;font-weight:900;letter-spacing:.5px}
.logo{width:42px;height:42px;border-radius:13px;background:linear-gradient(145deg,#70c7ff,#0b5cff);display:grid;place-items:center;box-shadow:0 8px 25px rgba(72,169,255,.35)}
.logo span{font-size:22px;font-weight:1000}
.lang{display:flex;align-items:center;gap:8px}
select,button,input,textarea{font:inherit}
select{border:1px solid rgba(255,255,255,.2);background:#10264d;color:white;border-radius:10px;padding:9px 12px}
main{max-width:1180px;margin:auto;padding:28px 20px 70px}
.hero{
  position:relative;overflow:hidden;border-radius:30px;padding:32px;
  background:linear-gradient(135deg,#061735,#0b5cff 62%,#52b7ff);
  color:white;box-shadow:var(--shadow);margin-bottom:22px
}
.hero:after{content:"";position:absolute;width:270px;height:270px;border:42px solid rgba(255,255,255,.09);border-radius:50%;right:-65px;top:-110px}
.kicker{font-weight:800;color:#aee0ff;letter-spacing:2px;font-size:12px;text-transform:uppercase}
.hero h1{font-size:clamp(32px,5vw,60px);margin:6px 0 5px;line-height:1}
.hero p{max-width:720px;color:#dceeff;margin:10px 0 20px;line-height:1.7}
.hero-actions{display:flex;flex-wrap:wrap;gap:10px}
.btn{
  border:0;border-radius:12px;padding:11px 16px;font-weight:800;cursor:pointer;
  background:white;color:#0b5cff;transition:.2s transform,.2s box-shadow
}
.btn:hover{transform:translateY(-2px);box-shadow:0 8px 20px rgba(0,0,0,.15)}
.btn.secondary{background:rgba(255,255,255,.12);color:white;border:1px solid rgba(255,255,255,.2)}
.grid{display:grid;grid-template-columns:repeat(12,1fr);gap:18px}
.card{
  grid-column:span 12;background:var(--card);border:1px solid var(--line);border-radius:22px;
  padding:22px;box-shadow:var(--shadow);backdrop-filter:blur(8px)
}
.card.half{grid-column:span 6}.card.third{grid-column:span 4}
.card-head{display:flex;justify-content:space-between;align-items:center;gap:10px;margin-bottom:16px}
.card h2{margin:0;font-size:19px}.badge{padding:5px 9px;border-radius:999px;background:#e5f2ff;color:#0b5cff;font-size:12px;font-weight:800}
.fields{display:grid;grid-template-columns:repeat(2,1fr);gap:13px}
.field.full{grid-column:1/-1}
label{display:block;font-size:12px;font-weight:800;color:#496180;margin-bottom:6px}
input,textarea{
  width:100%;border:1px solid #c9def5;border-radius:12px;padding:11px 12px;
  background:#f9fcff;color:var(--ink);outline:none
}
input:focus,textarea:focus{border-color:#48a9ff;box-shadow:0 0 0 3px rgba(72,169,255,.14)}
textarea{min-height:100px;resize:vertical}
.section-icon{width:36px;height:36px;border-radius:10px;background:#e8f4ff;color:#0b5cff;display:grid;place-items:center;font-size:18px}
.timeline{border-left:3px solid #b9ddff;margin:5px 0 0 10px;padding-left:18px}
.timeline-item{position:relative;margin:0 0 18px}.timeline-item:before{content:"";position:absolute;left:-27px;top:5px;width:11px;height:11px;border-radius:50%;background:#0b5cff;border:3px solid white;box-shadow:0 0 0 2px #8bc9ff}
.small{font-size:12px;color:#66809f}
.notice{background:#fff8e8;border:1px solid #ffe2a5;border-radius:13px;padding:12px;color:#715116;font-size:12px;line-height:1.6}
footer{text-align:center;color:#66809f;font-size:12px;padding:28px 10px}
@media(max-width:800px){.card.half,.card.third{grid-column:span 12}.fields{grid-template-columns:1fr}.hero{padding:25px 21px}.nav{padding:10px 14px}}
@media print{
  header,.hero-actions,.notice,.no-print{display:none!important}
  body{background:white}.card{box-shadow:none;break-inside:avoid}.hero{display:block;background:white;color:black;padding:0;border-bottom:2px solid #0b5cff}
  .hero p{color:#333}
}
</style>
</head>
<body>
<header>
  <div class="nav">
    <div class="brand"><div class="logo"><span>+</span></div><span id="brandText">翔・隨身電子病歷</span></div>
    <div class="lang">
      <span id="languageLabel" style="font-size:12px;color:#cfe4ff">語言</span>
      <select id="languageSelect" aria-label="Language">
        <option value="zh-TW">繁體中文</option><option value="en">English</option>
        <option value="ko">한국어</option><option value="ja">日本語</option><option value="vi">Tiếng Việt</option>
      </select>
    </div>
  </div>
</header>

<main>
<section class="hero">
  <div class="kicker" id="heroKicker">PERSONAL MEDICAL RECORD</div>
  <h1 id="heroTitle">翔的隨身電子病歷</h1>
  <p id="heroDesc">一個以藍色系超級英雄漫畫氛圍為靈感的個人健康資料中心。所有內容都保留在此 HTML 頁面中，可自行編輯。</p>
  <div class="hero-actions">
    <button class="btn" onclick="window.print()" id="printBtn">列印 / 儲存 PDF</button>
    <button class="btn secondary" onclick="document.getElementById('personal').scrollIntoView()" id="editBtn">開始編輯</button>
  </div>
</section>

<div class="grid">
  <section class="card half" id="personal">
    <div class="card-head"><div style="display:flex;gap:10px;align-items:center"><div class="section-icon">👤</div><h2 data-i18n="personal">個人資料</h2></div><span class="badge">ID</span></div>
    <div class="fields">
      <div><label data-i18n="name">姓名</label><input value="盛翔"></div>
      <div><label data-i18n="dob">出生日期</label><input type="date" value="2010-11-20"></div>
      <div><label data-i18n="blood">血型</label><input value="O"></div>
      <div><label data-i18n="sex">生理性別</label><input placeholder="請自行填寫"></div>
      <div class="field full"><label data-i18n="idno">身分證 / 護照號碼（選填）</label><input placeholder="不建議在公開或共享裝置輸入"></div>
      <div class="field full"><label data-i18n="contact">聯絡方式</label><input placeholder="電話 / Email / 其他"></div>
    </div>
  </section>

  <section class="card half">
    <div class="card-head"><div style="display:flex;gap:10px;align-items:center"><div class="section-icon">🚨</div><h2 data-i18n="emergency">緊急資訊</h2></div><span class="badge" data-i18n="important">重要</span></div>
    <div class="fields">
      <div class="field full"><label data-i18n="allergy">過敏 / 不良反應</label><textarea placeholder="藥物、食物、環境等"></textarea></div>
      <div class="field full"><label data-i18n="emergencyContact">緊急聯絡人</label><input placeholder="姓名 / 關係 / 電話"></div>
      <div class="field full"><label data-i18n="special">重要醫療提醒</label><textarea placeholder="例如：需要特別注意的事項"></textarea></div>
    </div>
  </section>

  <section class="card third">
    <div class="card-head"><div class="section-icon">🩺</div><h2 data-i18n="disease">疾病史</h2></div>
    <label data-i18n="diseaseText">既往疾病 / 慢性疾病</label><textarea></textarea>
  </section>
  <section class="card third">
    <div class="card-head"><div class="section-icon">🧬</div><h2 data-i18n="family">家族史</h2></div>
    <label data-i18n="familyText">家族疾病 / 遺傳相關資訊</label><textarea></textarea>
  </section>
  <section class="card third">
    <div class="card-head"><div class="section-icon">💊</div><h2 data-i18n="meds">用藥史</h2></div>
    <label data-i18n="medText">目前 / 過去使用藥物</label><textarea></textarea>
  </section>

  <section class="card half">
    <div class="card-head"><div style="display:flex;gap:10px;align-items:center"><div class="section-icon">🏥</div><h2 data-i18n="surgery">手術與住院史</h2></div></div>
    <div class="timeline">
      <div class="timeline-item"><label data-i18n="surgery1">手術 / 住院紀錄 1</label><input placeholder="日期｜醫療院所｜原因｜結果"></div>
      <div class="timeline-item"><label data-i18n="surgery2">手術 / 住院紀錄 2</label><input placeholder="日期｜醫療院所｜原因｜結果"></div>
      <div class="timeline-item"><label data-i18n="surgery3">其他紀錄</label><input placeholder="可繼續新增"></div>
    </div>
  </section>

  <section class="card half">
    <div class="card-head"><div style="display:flex;gap:10px;align-items:center"><div class="section-icon">💉</div><h2 data-i18n="vaccine">疫苗與預防保健</h2></div></div>
    <div class="fields">
      <div class="field full"><label data-i18n="vaccineText">疫苗接種紀錄</label><textarea placeholder="疫苗名稱｜日期｜劑次"></textarea></div>
      <div class="field full"><label data-i18n="checkup">健檢 / 篩檢</label><textarea placeholder="日期｜檢查項目｜結果"></textarea></div>
    </div>
  </section>

  <section class="card half">
    <div class="card-head"><div style="display:flex;gap:10px;align-items:center"><div class="section-icon">🧪</div><h2 data-i18n="labs">檢驗與重要數據</h2></div></div>
    <div class="fields">
      <div><label data-i18n="height">身高</label><input placeholder="cm"></div>
      <div><label data-i18n="weight">體重</label><input placeholder="kg"></div>
      <div><label data-i18n="bp">血壓</label><input placeholder="例如 120/80"></div>
      <div><label data-i18n="pulse">脈搏</label><input placeholder="次 / 分"></div>
      <div class="field full"><label data-i18n="labText">其他重要檢驗結果</label><textarea></textarea></div>
    </div>
  </section>

  <section class="card half">
    <div class="card-head"><div style="display:flex;gap:10px;align-items:center"><div class="section-icon">📝</div><h2 data-i18n="lifestyle">生活與健康習慣</h2></div></div>
    <div class="fields">
      <div class="field full"><label data-i18n="lifestyleText">睡眠、運動、飲食等</label><textarea></textarea></div>
      <div class="field full"><label data-i18n="notes">其他備註</label><textarea></textarea></div>
    </div>
  </section>

  <section class="card">
    <div class="card-head"><div style="display:flex;gap:10px;align-items:center"><div class="section-icon">📚</div><h2 data-i18n="more">建議補充的醫療資訊</h2></div></div>
    <div class="fields">
      <div><label data-i18n="diagnosis">重要診斷 / 檢查報告</label><input></div>
      <div><label data-i18n="doctor">常看的醫師 / 科別</label><input></div>
      <div><label data-i18n="device">植入物 / 醫療器材</label><input></div>
      <div><label data-i18n="organ">器官捐贈意願（選填）</label><input></div>
      <div><label data-i18n="insurance">保險資訊（選填）</label><input></div>
      <div><label data-i18n="pharmacy">常用藥局 / 醫療院所</label><input></div>
    </div>
  </section>

  <section class="card">
    <div class="notice" id="privacyNotice">
      隱私提醒：這是一個純前端靜態頁面。資料會留在你目前使用的瀏覽器頁面中，不會自動上傳到伺服器；請避免在公開電腦留下敏感醫療資料。這個頁面不能取代正式醫療紀錄。
    </div>
  </section>
</div>
<footer id="footerText">翔・Personal Medical Record · 靜態 HTML / CSS / JavaScript</footer>
</main>

<script>
const translations = {
 "zh-TW":{
  brand:"翔・隨身電子病歷", heroKicker:"PERSONAL MEDICAL RECORD", heroTitle:"翔的隨身電子病歷",
  heroDesc:"一個以藍色系超級英雄漫畫氛圍為靈感的個人健康資料中心。所有內容都保留在此 HTML 頁面中，可自行編輯。",
  language:"語言",print:"列印 / 儲存 PDF",edit:"開始編輯",personal:"個人資料",name:"姓名",dob:"出生日期",blood:"血型",
  sex:"生理性別",idno:"身分證 / 護照號碼（選填）",contact:"聯絡方式",emergency:"緊急資訊",important:"重要",
  allergy:"過敏 / 不良反應",emergencyContact:"緊急聯絡人",special:"重要醫療提醒",disease:"疾病史",diseaseText:"既往疾病 / 慢性疾病",
  family:"家族史",familyText:"家族疾病 / 遺傳相關資訊",meds:"用藥史",medText:"目前 / 過去使用藥物",
  surgery:"手術與住院史",surgery1:"手術 / 住院紀錄 1",surgery2:"手術 / 住院紀錄 2",surgery3:"其他紀錄",
  vaccine:"疫苗與預防保健",vaccineText:"疫苗接種紀錄",checkup:"健檢 / 篩檢",labs:"檢驗與重要數據",height:"身高",weight:"體重",
  bp:"血壓",pulse:"脈搏",labText:"其他重要檢驗結果",lifestyle:"生活與健康習慣",lifestyleText:"睡眠、運動、飲食等",
  notes:"其他備註",more:"建議補充的醫療資訊",diagnosis:"重要診斷 / 檢查報告",doctor:"常看的醫師 / 科別",
  device:"植入物 / 醫療器材",organ:"器官捐贈意願（選填）",insurance:"保險資訊（選填）",pharmacy:"常用藥局 / 醫療院所",
  privacy:"隱私提醒：這是一個純前端靜態頁面。資料會留在你目前使用的瀏覽器頁面中，不會自動上傳到伺服器；請避免在公開電腦留下敏感醫療資料。這個頁面不能取代正式醫療紀錄。",
  footer:"翔・Personal Medical Record · 靜態 HTML / CSS / JavaScript"
 },
 "en":{
  brand:"Xiang · Personal Medical Record",heroKicker:"PERSONAL MEDICAL RECORD",heroTitle:"Xiang's Personal Medical Record",
  heroDesc:"A blue superhero-comic-inspired personal health dashboard. Everything stays inside this HTML page and can be edited.",
  language:"Language",print:"Print / Save PDF",edit:"Edit Record",personal:"Personal Information",name:"Name",dob:"Date of Birth",blood:"Blood Type",
  sex:"Sex",idno:"ID / Passport (optional)",contact:"Contact",emergency:"Emergency Information",important:"IMPORTANT",
  allergy:"Allergies / Adverse Reactions",emergencyContact:"Emergency Contact",special:"Important Medical Notes",disease:"Medical History",
  diseaseText:"Previous / Chronic Conditions",family:"Family History",familyText:"Family Diseases / Genetic Information",meds:"Medication History",
  medText:"Current / Previous Medications",surgery:"Surgery & Hospitalization",surgery1:"Surgery / Hospitalization 1",surgery2:"Surgery / Hospitalization 2",
  surgery3:"Other Record",vaccine:"Vaccines & Preventive Care",vaccineText:"Vaccination Record",checkup:"Checkups / Screening",labs:"Labs & Key Measurements",
  height:"Height",weight:"Weight",bp:"Blood Pressure",pulse:"Pulse",labText:"Other Important Results",lifestyle:"Lifestyle & Health Habits",
  lifestyleText:"Sleep, exercise, diet, etc.",notes:"Other Notes",more:"Additional Medical Information",diagnosis:"Key Diagnoses / Reports",
  doctor:"Regular Doctor / Specialty",device:"Implants / Medical Devices",organ:"Organ Donation (optional)",insurance:"Insurance (optional)",
  pharmacy:"Usual Pharmacy / Medical Facility",privacy:"Privacy note: This is a frontend-only static page. Data is not automatically uploaded to a server. Avoid entering sensitive medical data on shared/public computers. This page does not replace official medical records.",
  footer:"Xiang · Personal Medical Record · Static HTML / CSS / JavaScript"
 },
 "ko":{
  brand:"翔 · 개인 의료 기록",heroKicker:"PERSONAL MEDICAL RECORD",heroTitle:"翔의 개인 의료 기록",
  heroDesc:"블루 계열의 슈퍼히어로 코믹 분위기에서 영감을 받은 개인 건강 기록 페이지입니다. 모든 내용은 이 HTML에서 직접 편집할 수 있습니다.",
  language:"언어",print:"인쇄 / PDF 저장",edit:"기록 편집",personal:"개인 정보",name:"이름",dob:"생년월일",blood:"혈액형",sex:"성별",
  idno:"신분증 / 여권 (선택)",contact:"연락처",emergency:"응급 정보",important:"중요",allergy:"알레르기 / 이상 반응",emergencyContact:"응급 연락처",
  special:"중요 의료 메모",disease:"질병력",diseaseText:"과거 / 만성 질환",family:"가족력",familyText:"가족 질환 / 유전 정보",
  meds:"복약력",medText:"현재 / 과거 복용 약물",surgery:"수술 및 입원력",surgery1:"수술 / 입원 기록 1",surgery2:"수술 / 입원 기록 2",surgery3:"기타 기록",
  vaccine:"예방접종 및 예방관리",vaccineText:"예방접종 기록",checkup:"건강검진 / 선별검사",labs:"검사 및 주요 수치",height:"키",weight:"체중",
  bp:"혈압",pulse:"맥박",labText:"기타 주요 검사 결과",lifestyle:"생활 습관",lifestyleText:"수면, 운동, 식습관 등",notes:"기타 메모",
  more:"추가 의료 정보",diagnosis:"주요 진단 / 검사 보고서",doctor:"주치의 / 진료과",device:"삽입물 / 의료기기",organ:"장기 기증 의향 (선택)",
  insurance:"보험 정보 (선택)",pharmacy:"주 이용 약국 / 의료기관",privacy:"개인정보 안내: 이 페이지는 프론트엔드 정적 페이지입니다. 데이터가 서버로 자동 업로드되지 않습니다. 공용 컴퓨터에는 민감한 의료 정보를 입력하지 마세요. 공식 의료 기록을 대체하지 않습니다.",
  footer:"翔 · Personal Medical Record · 정적 HTML / CSS / JavaScript"
 },
 "ja":{
  brand:"翔・携帯用電子カルテ",heroKicker:"PERSONAL MEDICAL RECORD",heroTitle:"翔の携帯用電子カルテ",
  heroDesc:"青系のスーパーヒーローコミックの雰囲気から着想を得た個人健康記録ページです。HTML内で直接編集できます。",
  language:"言語",print:"印刷 / PDF保存",edit:"編集開始",personal:"個人情報",name:"氏名",dob:"生年月日",blood:"血液型",sex:"性別",
  idno:"身分証 / パスポート（任意）",contact:"連絡先",emergency:"緊急情報",important:"重要",allergy:"アレルギー / 副作用",emergencyContact:"緊急連絡先",
  special:"重要な医療メモ",disease:"既往歴",diseaseText:"過去 / 慢性疾患",family:"家族歴",familyText:"家族の病気 / 遺伝情報",
  meds:"服薬歴",medText:"現在 / 過去の服薬",surgery:"手術・入院歴",surgery1:"手術 / 入院記録 1",surgery2:"手術 / 入院記録 2",surgery3:"その他の記録",
  vaccine:"予防接種・予防医療",vaccineText:"予防接種記録",checkup:"健康診断 / 検診",labs:"検査・主要データ",height:"身長",weight:"体重",
  bp:"血圧",pulse:"脈拍",labText:"その他の重要な検査結果",lifestyle:"生活習慣",lifestyleText:"睡眠、運動、食事など",notes:"その他のメモ",
  more:"追加の医療情報",diagnosis:"主な診断 / 検査報告",doctor:"主治医 / 診療科",device:"インプラント / 医療機器",organ:"臓器提供の意思（任意）",
  insurance:"保険情報（任意）",pharmacy:"よく利用する薬局 / 医療機関",privacy:"プライバシー注意：これはフロントエンドのみの静的ページです。データはサーバーへ自動送信されません。共有・公共の端末では機密性の高い医療情報を入力しないでください。正式な医療記録の代わりにはなりません。",
  footer:"翔・Personal Medical Record · 静的 HTML / CSS / JavaScript"
 },
 "vi":{
  brand:"翔 · Hồ sơ y tế cá nhân",heroKicker:"PERSONAL MEDICAL RECORD",heroTitle:"Hồ sơ y tế cá nhân của 翔",
  heroDesc:"Trang hồ sơ sức khỏe cá nhân lấy cảm hứng từ không khí truyện tranh siêu anh hùng tông xanh. Bạn có thể chỉnh sửa trực tiếp trong HTML này.",
  language:"Ngôn ngữ",print:"In / Lưu PDF",edit:"Chỉnh sửa",personal:"Thông tin cá nhân",name:"Họ tên",dob:"Ngày sinh",blood:"Nhóm máu",
  sex:"Giới tính",idno:"CCCD / Hộ chiếu (tùy chọn)",contact:"Liên hệ",emergency:"Thông tin khẩn cấp",important:"QUAN TRỌNG",
  allergy:"Dị ứng / Phản ứng bất lợi",emergencyContact:"Liên hệ khẩn cấp",special:"Lưu ý y tế quan trọng",disease:"Tiền sử bệnh",
  diseaseText:"Bệnh trước đây / bệnh mạn tính",family:"Tiền sử gia đình",familyText:"Bệnh gia đình / thông tin di truyền",meds:"Tiền sử dùng thuốc",
  medText:"Thuốc đang / đã sử dụng",surgery:"Phẫu thuật & nhập viện",surgery1:"Phẫu thuật / nhập viện 1",surgery2:"Phẫu thuật / nhập viện 2",surgery3:"Ghi chú khác",
  vaccine:"Tiêm chủng & phòng bệnh",vaccineText:"Lịch sử tiêm chủng",checkup:"Khám sức khỏe / sàng lọc",labs:"Xét nghiệm & chỉ số",
  height:"Chiều cao",weight:"Cân nặng",bp:"Huyết áp",pulse:"Mạch",labText:"Kết quả xét nghiệm quan trọng khác",lifestyle:"Lối sống & thói quen sức khỏe",
  lifestyleText:"Giấc ngủ, vận động, ăn uống...",notes:"Ghi chú khác",more:"Thông tin y tế bổ sung",diagnosis:"Chẩn đoán / báo cáo quan trọng",
  doctor:"Bác sĩ / chuyên khoa thường khám",device:"Vật cấy ghép / thiết bị y tế",organ:"Nguyện vọng hiến tạng (tùy chọn)",
  insurance:"Thông tin bảo hiểm (tùy chọn)",pharmacy:"Nhà thuốc / cơ sở y tế thường dùng",privacy:"Lưu ý riêng tư: Đây là trang tĩnh chỉ chạy ở phía trình duyệt. Dữ liệu không tự động được tải lên máy chủ. Không nhập dữ liệu y tế nhạy cảm trên máy tính công cộng hoặc dùng chung. Trang này không thay thế hồ sơ y tế chính thức.",
  footer:"翔 · Personal Medical Record · HTML / CSS / JavaScript tĩnh"
 }
};

function applyLang(lang){
  const t=translations[lang];
  document.documentElement.lang=lang;
  document.getElementById("brandText").textContent=t.brand;
  document.getElementById("heroKicker").textContent=t.heroKicker;
  document.getElementById("heroTitle").textContent=t.heroTitle;
  document.getElementById("heroDesc").textContent=t.heroDesc;
  document.getElementById("languageLabel").textContent=t.language;
  document.getElementById("printBtn").textContent=t.print;
  document.getElementById("editBtn").textContent=t.edit;
  document.querySelectorAll("[data-i18n]").forEach(el=>{const k=el.dataset.i18n;if(t[k])el.textContent=t[k]});
  document.getElementById("privacyNotice").textContent=t.privacy;
  document.getElementById("footerText").textContent=t.footer;
  localStorage.setItem("medicalLang",lang);
}
document.getElementById("languageSelect").addEventListener("change",e=>applyLang(e.target.value));
const saved=localStorage.getItem("medicalLang")||"zh-TW";
document.getElementById("languageSelect").value=saved;
applyLang(saved);
</script>
</body>
</html>
