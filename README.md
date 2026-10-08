# Prompt Enhancement for PI-Desktop

An optional PI-Desktop plugin that adds an **Enhance prompt** action to the
Composer. It is not bundled with PI-Desktop and is never enabled by the app by
default. Install it only if you want this feature.

When clicked, the plugin sends the current draft text to the selected model
provider through the host's `agent.complete` service. It does not read the
conversation history or file attachments. The host keeps file-reference chips
out of the request and preserves them when applying the returned text. One
undo action restores the previous draft.

## Permissions

- `composer.transform` lets the host show a plugin-owned Composer action and
  apply its result only while the draft has not changed.
- `agent.complete` lets the plugin request a one-shot completion using a model
  already configured in PI-Desktop. API keys remain in the host.

The draft text is sent to the configured provider after you click **Enhance
prompt**. The plugin does not send anything automatically.

## Install from this repository

1. Clone this repository.
2. In PI-Desktop, open **Plugins** and choose **Load local plugin** from the
   top-right actions menu.
3. Select the cloned repository folder and review the requested permissions.
   Grant `composer.transform` and `agent.complete` to use prompt enhancement.

## Settings

- **Enhancement model**: blank follows the model selected in the Composer; set
  `providerId/modelId` to pin another model.
- **Reasoning effort**: defaults to Off.
- **Custom user template**: blank uses the included template. A custom template
  must contain `{{draft}}` and be at most 8,000 characters. The plugin's
  settings sheet provides a multiline editor.

The system prompt remains fixed so the task, language, and output rules stay
consistent. Plugin settings are stored in PI-Desktop's private plugin settings.

## Development

This repository contains the plugin source independently of PI-Desktop and its
marketplace distribution repository. Marketplace installation can be offered
as an opt-in only after publishing a tagged release through the PI-Desktop
plugin center.

The manifest requires PI-Desktop 0.1.0 or later and has no build step.

## License

GNU Lesser General Public License v3.0. See `LICENSE`.
