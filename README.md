# ชุด Skills สำหรับ Codex: ทำเกม ออกแบบ UI และพัฒนาซอฟต์แวร์

รวม **frontend-design, Impeccable, Superpowers, pstack Game Studio และ game-storyboard** สำหรับให้เพื่อนติดตั้ง ใช้ได้ทั้งงานเว็บ เกม 2D/3D และเตรียมโมเดลจาก Blender

ชุดนี้ปรับเป็น **Low-token edition**: งานทั่วไปใช้ GPT‑6.1 Sol แบบ Low/Light งานยากใช้ GPT‑6 Astra แบบ Low/Light และ workflow หนักต้องเรียกอย่างชัดเจน กฎฉบับเต็มอยู่ใน [LOW_TOKEN_RULES.md](./LOW_TOKEN_RULES.md) พร้อม [ค่าตั้งต้น](./low-token.config.toml)

ชุดนี้รวบรวม skills จากเจ้าของต้นฉบับ และเพิ่ม game-storyboard ที่สร้างสำหรับ starter pack นี้ และไม่ใช่ชุดปลั๊กอินที่ติดตั้ง integrations ทุกตัวให้อัตโนมัติ

## ติดตั้งง่ายที่สุด

1. ติดตั้ง Codex และเข้าสู่ระบบก่อน
2. ดาวน์โหลด [skills-bundle.zip](./skills-bundle.zip) แล้วแตก ZIP ไปยังโฟลเดอร์ที่ Codex เข้าถึงได้
3. เปิดแชต Codex ในโฟลเดอร์นั้น แล้ววางข้อความนี้:

```text
ช่วยติดตั้ง skills ทุกชุดจาก ZIP ที่แตกไว้ ได้แก่ frontend-design,
Impeccable, Superpowers, pstack, Game Studio และ game-storyboard สำหรับผู้ใช้คนนี้
ตรวจ SOURCES.json เพื่อดูแหล่งต้นฉบับ
เก็บโครงสร้างของแต่ละชุดไว้ใน ~/.codex/skill-bundles แล้วทำให้ Codex
ค้นพบแต่ละ skill ผ่าน ~/.codex/skills โดยใช้ symlink บน macOS/Linux
หรือ junction/วิธีที่รองรับบน Windows
ต้องเก็บ references, scripts, assets, agents และไฟล์ประกอบที่ถูกอ้างถึงครบ
ตรวจ relative paths จากตำแหน่งติดตั้งจริง
อ่าน LOW_TOKEN_RULES.md และเพิ่มเป็น user preferences ใน ~/.codex/AGENTS.md
โดยรักษากฎอื่นที่มีอยู่ ถ้าขัดกันให้แสดงจุดขัดแย้งก่อนแก้
รวมค่าจาก low-token.config.toml เข้า ~/.codex/config.toml
โดยสำรองไฟล์ก่อนและรักษา credentials, tools, projects และ settings อื่น
เก็บ agents/openai.yaml ที่กำหนด allow_implicit_invocation: false ไว้
อย่าเขียนทับ skills เดิม ถ้าชื่อชนให้แจ้งและแยกชื่อชุดใหม่
ถ้าเปลี่ยนชื่อ ให้ปรับ name และการอ้างอิงระหว่าง skills ให้ตรงกันด้วย
อย่าเปิด hooks, automation หรือ integrations อัตโนมัติ
ปรับ model settings เฉพาะ low-token preset ที่ระบุด้านบน
ตรวจว่าไฟล์ติดตั้งครบ แล้วบอกชื่อ skill ที่เรียกใช้งานได้
```

ส่งข้อความใหม่หลังติดตั้ง ถ้า skills ยังไม่ปรากฏ ให้เปิดแชตใหม่หรือรีสตาร์ต Codex

## การใช้โมเดลและควบคุม tokens

ใช้ **Generate → Verify → Repair**: กำหนดเกณฑ์ผ่าน สร้าง ตรวจผลจริง แก้เฉพาะจุดที่ไม่ผ่าน แล้วตรวจซ้ำ งาน motion ตรวจ timing, easing, stagger, ระยะเคลื่อนที่ และ overshoot จากเฟรมจริง ตาม [คู่มือ Motion Verification](./MOTION_VERIFICATION.md) เริ่มด้วยการตรวจหนึ่งรอบและแก้สองชุด หากยังไม่ผ่านให้ทบทวนสาเหตุ ไม่วนปรับค่าเดิมหรือรายงานว่าเสร็จทั้งที่ตรวจไม่ได้

| งาน | โมเดล | Reasoning |
|---|---|---|
| งานทั่วไป เขียนโค้ด แก้ไฟล์ และรีวิวทั่วไป | `gpt-6.1-sol` | `low` / Light |
| บั๊กซับซ้อน concurrency อัลกอริทึม หรือการตัดสินใจสถาปัตยกรรมที่ยาก | `gpt-6-astra` | `low` / Light |

CLI ใช้ `codex --profile lean` หรือ `codex --profile hard` หลังรวม config แล้ว ในแอปเลือกโมเดลและ Light/Low จากตัวเลือกของแชต โปรไฟล์เป็นค่าเริ่มต้น ไม่ใช่ตัวสลับโมเดลอัตโนมัติ และไม่เปลี่ยนโมเดลของแชตที่เปิดอยู่เอง

ใช้ agent เดียวเป็นหลัก เลือก pstack หรือ Superpowers เพียง workflow เดียว งานทั่วไปไม่บังคับ brainstorm, TDD หรือ reviewer panel ทุกครั้ง งานยากอาจมอบหมายส่วนที่จำเป็นให้ Astra low หนึ่งตัวเมื่ออนุญาตให้ใช้ subagent แล้ว ใช้บริบทสั้นเฉพาะงาน

Skills ที่ซ้ำหรือใช้กระบวนการหนักตั้งเป็น explicit-only ผ่าน `agents/openai.yaml` จึงเรียกด้วยชื่อได้เมื่อจำเป็น ส่วน using-superpowers, brainstorming, test-driven-development, requesting-code-review และ setup-pstack ถูกปรับคำสั่งให้ตรงกับกฎชุดนี้ เก็บหลักฐานการตรวจงานและข้อกำหนดความปลอดภัยไว้ตามเดิม ไม่มีการรับประกันเปอร์เซ็นต์การประหยัด tokens

## มีอะไรบ้าง

| ชุด | ใช้ทำอะไร | ต้นฉบับ |
|---|---|---|
| frontend-design | กำหนดทิศทางภาพและออกแบบ UI | [Anthropic](https://github.com/anthropics/skills/tree/main/skills/frontend-design) |
| Impeccable | ออกแบบ ตรวจ และปรับ UI เช่น audit, critique, polish | [pbakaus/impeccable](https://github.com/pbakaus/impeccable) |
| Superpowers | วางแผน แก้บั๊ก ทดสอบ และตรวจงานพัฒนา | [obra/superpowers](https://github.com/obra/superpowers) |
| pstack | workflow วิศวกรรม เช่น poteto-mode, how, why, arena, interrogate | [Cursor pstack](https://github.com/cursor/plugins/tree/main/pstack) |
| Game Studio | เกม 2D ด้วย Phaser และ 3D ด้วย Three.js / React Three Fiber | [OpenAI Game Studio](https://github.com/openai/plugins/tree/main/plugins/game-studio) |

Game Studio มี 9 skills: game-studio, web-game-foundations, phaser-2d-game, three-webgl-game, react-three-fiber-game, web-3d-asset-pipeline, sprite-pipeline, game-ui-frontend และ game-playtest

game-storyboard เป็น custom skill สำหรับวางฉาก ตารางช็อต ภาพ storyboard และจังหวะส่งคืนการควบคุมให้ผู้เล่น ใช้ ImageGen หรือ Blender เมื่อจำเป็น ไม่ใช่ skill ทางการของ OpenAI และไม่ติดตั้ง Storyboarder/Twine อัตโนมัติ ดู [คำสั่ง skill](./skills/game-storyboard/SKILL.md)

## เตรียม Blender และเครื่องมือ 3D

ตัว ZIP มี skills และไฟล์ประกอบ ไม่รวม Blender, Node.js หรือโมเดล AI

1. ดาวน์โหลด [Blender จากเว็บไซต์ทางการ](https://www.blender.org/download/) เลือกให้ตรงกับระบบปฏิบัติการและ CPU
2. ติดตั้ง [Node.js รุ่น LTS](https://nodejs.org/) เพื่อใช้เครื่องมือเว็บเกมและ npm
3. เมื่อต้องลดขนาดโมเดล ใช้ [glTF Transform](https://gltf-transform.dev/cli):

```sh
npm install --global @gltf-transform/cli
gltf-transform --version
```

เก็บต้นฉบับเป็น `.blend` และส่งออก `.glb` หรือ glTF 2.0 สำหรับเกมเว็บ ตรวจ scale, pivot, materials, textures และ animations ก่อนนำเข้าเกม

## ตัวอย่างข้อความเริ่มงาน

```text
$game-storyboard วาง storyboard เปิดเกมผจญภัย 3D ความยาว 30 วินาที
ทำตาราง 6 ช็อต ระบุมุมกล้อง แอ็กชัน เสียง และจังหวะเริ่มควบคุมตัวละคร
เริ่มจากข้อความก่อน ยังไม่ต้องสร้างภาพ
```

```text
$game-studio ทำเกม 2D แนว platformer ด้วย Phaser
เริ่มจากเกมสั้นหนึ่งด่าน พร้อมเมนูเริ่มเกมและระบบเริ่มใหม่
```

```text
$game-studio ทำเกม 3D แนวสำรวจด้วย Three.js
ใช้ Blender ทำโมเดล low-poly และส่งออก GLB
```

```text
$web-3d-asset-pipeline สร้างบ้าน low-poly ด้วย Blender
เก็บไฟล์ .blend และส่งออก .glb สำหรับใช้ในเกม
```

```text
$impeccable audit ตรวจ UI หน้านี้
```

```text
$poteto-mode ตรวจว่าระบบ login ทำงานอย่างไร
อธิบายพร้อมหลักฐานจากโค้ด ยังไม่ต้องแก้
```

ชื่อที่แสดงในเมนู skills อาจมี prefix ของปลั๊กอิน ให้เลือกชื่อที่ Codex แสดงจริงหลังติดตั้ง

## ขอบเขตและแหล่งที่มา

- pstack มีส่วนเฉพาะ Cursor เช่น model routing, history และ automation ซึ่งต้องปรับให้เข้ากับ Codex; การคัดลอก skills ไม่ทำให้ integrations เหล่านี้พร้อมใช้ทั้งหมด
- Impeccable อาจดาวน์โหลด engine ทางการเมื่อใช้งานครั้งแรก แต่ชุดนี้ไม่เปิด hooks ให้เอง
- การใช้งาน image generation, browser tools, หลายโมเดล หรือบริการภายนอกขึ้นกับเครื่องมือและสิทธิ์ของบัญชีเพื่อน
- ไม่รวมการตั้งค่าเครื่อง บัญชี ประวัติแชต credentials หรือ skills ส่วนตัวของผู้รวบรวม
- ZIP เก็บไฟล์ license/notice จากต้นฉบับ ข้อกำหนดแต่ละชุดยังใช้ตามเจ้าของเดิม ไม่ได้เปลี่ยน license ให้เป็นแบบเดียวกัน
- [SOURCES.json](./SOURCES.json) ระบุ repository และข้อมูล snapshot ที่ใช้ ชุดนี้เป็น snapshot; อัปเดตจากต้นฉบับเมื่อต้องการเวอร์ชันใหม่
- Skills บางส่วนปรับจากต้นฉบับเพื่อใช้ low-token policy ดังที่อธิบายด้านบน หากอัปเดตจาก upstream ให้ทบทวน policy และ invocation metadata อีกครั้ง
