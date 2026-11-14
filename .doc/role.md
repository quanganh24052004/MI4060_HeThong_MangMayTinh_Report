# Quy Chuẩn Thuật Ngữ & Viết Tắt (Thesis Terminology & Abbreviations)

Tài liệu này định nghĩa quy trình và các nguyên tắc bắt buộc khi xử lý thuật ngữ khoa học và chữ viết tắt trong toàn bộ bản thảo đồ án/luận văn.

---

## 1. Nguyên Tắc Cốt Lõi (Core Rules)

### Quy tắc 1: Tuân thủ luật viết tắt (First Occurrence Rule)

- **Lần đầu tiên xuất hiện:** Bắt buộc định nghĩa đầy đủ theo định dạng: `Tên đầy đủ tiếng Việt (Từ viết tắt)` hoặc `Tên đầy đủ tiếng Anh (Từ viết tắt)`.
  - *Ví dụ:* `Trí tuệ nhân tạo (AI)` hoặc `International Phonetic Alphabet (IPA)`.
- **Từ lần thứ hai trở đi:** Chỉ sử dụng duy nhất từ viết tắt (ví dụ: `AI`, `IPA`), **tuyệt đối không** lặp lại phần định nghĩa đầy đủ.
- **Tính chọn lọc:** Không tự tiện tạo chữ viết tắt cho các cụm từ thông thường ít xuất hiện hoặc không mang tính chuyên ngành đặc thù.

### Quy tắc 2: Chống chú thích song ngữ tùy tiện (No Redundant Bilingual Glosses)

- **Tuyệt đối cấm:** Không sử dụng cấu trúc `Tiếng Việt (Thuật ngữ tiếng Anh)` trong thân bài (ví dụ: cấm viết *Nhận diện âm vị (Phoneme Recognition)* hoặc *học ngoại tuyến (Offline-first)*). Cách viết này gây rối mắt, phá vỡ tính mạch lạc học thuật và bị xem là chú thích bừa bãi.
- **Cách xử lý chuẩn:**
  1. **Ưu tiên thuần Việt:** Nếu thuật ngữ đã có bản dịch tiếng Việt chuẩn xác, phổ biến trong chuyên ngành, hãy dùng thuần tiếng Việt (ví dụ: *nhận diện âm vị*, *mạng nơ-ron tích chập*, *hồi quy*).
  2. **Giữ nguyên thuật ngữ tiếng Anh:** Nếu thuật ngữ chuyên sâu chưa có cách dịch tiếng Việt tương đương hoặc cách dịch gây tối nghĩa, hãy giữ nguyên thuật ngữ tiếng Anh và giải thích nếu cần ở bảng thuật ngữ (ví dụ: *offline-first*, *fine-tuning*, *transformer*, *zero-shot*).

### Quy tắc 3: Đồng bộ hóa danh mục viết tắt (`frontmatter/abbreviations.tex`)

- **Yêu cầu:** Mọi từ viết tắt xuất hiện trong bài thảo luận đều phải được khai báo trong bảng ký hiệu và chữ viết tắt tại file `frontmatter/abbreviations.tex`.
- **Cấu trúc hàng trong bảng LaTeX:**

  ```latex
  <TỪ_VIẾT_TẮT> & <Giải nghĩa đầy đủ (tiếng Anh hoặc tiếng Việt)>\\
  ```

  *Ví dụ:*

  ```latex
  AI & Artificial Intelligence\\
  GOP & Goodness of Pronunciation\\
  SRS & Spaced Repetition System\\
  ```

### Quy tắc 4: Biểu diễn 44 ký hiệu ngữ âm IPA với font Doulos SIL
- **Cấu hình font:** Toàn bộ 44 phiên âm IPA (20 nguyên âm và 24 phụ âm) trong dự án phải được bọc trong lệnh `\ipa{...}` để hiển thị đúng font Doulos SIL chuyên dụng (`setup/fonts/Doulos_SIL_Regular.ttf`).
- **Cấm dùng chế độ toán học:** Không dùng chế độ toán học (như `$/\theta/$` hay `$/i:/$`) để giả lập phiên âm. Sử dụng trực tiếp ký tự ngữ âm Unicode chuẩn đặt trong `\ipa{...}` (ví dụ: `\ipa{/θ/}`, `\ipa{/ð/}`, `\ipa{/ɪ/}`, `\ipa{/iː/}`).

---

## 2. Bảng Đối Chiếu Đúng / Sai (Examples & Anti-Patterns)

| Tình huống | Sai (Cần tránh) | Đúng (Chuẩn học thuật) | Ghi chú |
| --- | --- | --- | --- |
| **Lần đầu xuất hiện** | "Mô hình dùng AI để..." *(chưa định nghĩa)* | "Mô hình ứng dụng Trí tuệ nhân tạo (AI)..." | Phải có tên đầy đủ kèm từ viết tắt ở lần đầu. |
| **Các lần tiếp theo** | "Hệ thống Trí tuệ nhân tạo (AI) hoạt động..." | "Hệ thống AI hoạt động..." | Từ lần thứ hai chỉ dùng chữ viết tắt `AI`. |
| **Chú thích song ngữ** | "...sử dụng phương pháp nhận diện âm vị (Phoneme Recognition)." | "...sử dụng phương pháp nhận diện âm vị." | Bỏ hẳn phần tiếng Anh trong ngoặc. |
| **Thuật ngữ mượn** | "...kiến trúc học ngoại tuyến (Offline-first)..." | "...kiến trúc offline-first..." | Dùng thẳng từ tiếng Anh nếu không dịch. |
| **Dịch gượng ép** | "...cơ chế chú ý tự thân (Self-attention)..." | "...cơ chế self-attention..." | Dùng từ chuyên ngành chuẩn hóa. |

---

## 3. Quy Trình Rà Soát & Triển Khai (Workflow & Runbook)

Khi viết mới hoặc chỉnh sửa bất kỳ đoạn văn bản / file `.tex` nào, Agent thực hiện lần lượt 4 bước sau:

### Bước 1: Quét thuật ngữ & từ viết tắt mới

- Liệt kê các chữ viết tắt (viết hoa từ 2 chữ cái trở lên như `AI`, `CNN`, `NLP`, `SRS`,...) có trong đoạn dự định viết hoặc chỉnh sửa.
- Tra cứu trong toàn bộ dự án (`chapters/*.tex`) xem từ viết tắt này đã từng xuất hiện và được định nghĩa trước đó chưa.

### Bước 2: Chuẩn hóa cách trình bày trong văn bản

- Nếu là **lần đầu tiên** xuất hiện trong đồ án: Viết `Tên đầy đủ (Chữ viết tắt)`.
- Nếu đã xuất hiện trước đó: Chỉ viết `Chữ viết tắt`.
- Kiểm tra toàn bộ văn bản để xóa bỏ các cụm mở ngoặc tiếng Anh kiểu `Tiếng Việt (English)`.

### Bước 3: Đồng bộ file `frontmatter/abbreviations.tex`

- Đọc nội dung `frontmatter/abbreviations.tex`.
- Nếu từ viết tắt chưa có trong bảng:
  - Thêm một dòng mới: `<TỪ_VIẾT_TẮT> & <Giải nghĩa đầy đủ>\\`
  - Đảm bảo không trùng lặp và giữ định dạng căn lề nhất quán.

### Bước 4: Kiểm tra xác thực (Validation Checklist)

- [ ] Không còn cấu trúc dạng `Tiếng Việt (English)`.

- [ ] Từ viết tắt chỉ được giải thích ở lần đầu tiên.

- [ ] Mọi từ viết tắt đều có mặt trong `frontmatter/abbreviations.tex`.

- [ ] File `frontmatter/abbreviations.tex` biên dịch sạch (không lỗi cú pháp bảng).