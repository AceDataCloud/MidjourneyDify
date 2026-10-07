# Midjourney capability mapping

Compared with [MCPs at f0eed10abf31](https://github.com/AceDataCloud/MCPs/tree/f0eed10abf310824cb4c33d4944c63d3654ac95b/midjourney) and the public API contract at PlatformBackend `fa94598267a82545fb1afed6ee26bafd6cbb9ca7`.

The table maps service operations to Dify tools. Different MCP helper functions may use the same action selector or structured JSON input.

| MCP function | Dify equivalent | Notes |
|---|---|---|
| `midjourney_edit` | `midjourney_edits` | Set action=generate |
| `midjourney_get_seed` | `midjourney_get_seed` |  |
| `midjourney_imagine` | `midjourney_imagine` | Set action=generate |
| `midjourney_transform` | `midjourney_imagine` |  |
| `midjourney_blend` | `midjourney_imagine` | Set action=generate |
| `midjourney_with_reference` | `midjourney_imagine` | Set action=generate |
| `midjourney_shorten` | `midjourney_shorten` |  |
| `midjourney_list_actions` |  | Model/action selectors and the API reference; informational guidance does not submit a request. |
| `midjourney_get_prompt_guide` |  | Model/action selectors and the API reference; informational guidance does not submit a request. |
| `midjourney_list_transform_actions` |  | Model/action selectors and the API reference; informational guidance does not submit a request. |
| `midjourney_get_task` | `midjourney_task_retrieve` | Set action=retrieve |
| `midjourney_get_tasks_batch` | `midjourney_tasks_retrieve_batch` | Set action=retrieve_batch |
| `midjourney_translate` | `midjourney_translate` |  |
| `midjourney_describe` | `midjourney_describe` |  |
| `midjourney_generate_video` | `midjourney_videos` | Set action=generate |
| `midjourney_extend_video` | `midjourney_videos` | Set action=extend |

## Parameter equivalents

- `midjourney_edit`: `async_` → Dify submit/poll output: async=true, stream=false.
- `midjourney_imagine`: `async_` → Dify submit/poll output: async=true, stream=false.
- `midjourney_blend`: `image_urls` → prompt: prepend the reference image URL(s), as in the MCP.
- `midjourney_with_reference`: `reference_image_url` → prompt: prepend the reference image URL(s), as in the MCP.
- `midjourney_get_tasks_batch`: `task_ids` → ids.
- `midjourney_generate_video`: `async_` → Dify submit/poll output: async=true, stream=false.
- `midjourney_extend_video`: `async_` → Dify submit/poll output: async=true, stream=false.

## Verification boundary

Contract examples and regression tests cover request validation, transport and task handling. Actual Dify browser cases are recorded separately in `tests/e2e-results.json` and `tests/e2e-audit.json` when available. A schema test is not a successful paid generation. Unsupported service availability and untested advanced combinations must not be described as passed.
