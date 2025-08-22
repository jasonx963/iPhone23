# Pago y carga de comprobantes

## Despliegue rápido en Vercel
1. Asegúrate de tener **Vercel CLI** (`npm i -g vercel`).
2. Incluye las variables de KV en el proyecto (Project Settings → Storage → KV). Debes tener:
   - `KV_URL`
   - `KV_REST_API_URL`
   - `KV_REST_API_TOKEN`
   - `KV_REST_API_READ_ONLY_TOKEN` *(opcional)*
3. Ejecuta `npm install` para instalar `@vercel/kv` y `busboy`.
4. `vercel` 部署。

## Verificación
- 打开 `/api/health` 应返回 `{ ok: true }`。
- 点击「Contáctanos para comprar」应在新标签打开 `payment.html?product=...&productId=...`。
- 在支付页上传文件会 `POST /api/payment-upload`。若失败，请在 Network 面板查看 `status` 与 `response`。

## 常见问题
- 500/模块找不到：请先 `npm install` 并在 Vercel 中开启 `KV`，添加四个环境变量。
- 413/体积过大：请把文件控制在 8MB 以下（页面已经提示）。
- 405/Method not allowed：请确认请求是 POST 且路径为 `/api/payment-upload`。

