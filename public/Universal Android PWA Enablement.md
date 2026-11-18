# Universal Android PWA Enablement

> **Single-prompt mission.** Paste this prompt once. Then execute the entire mission yourself, from first inspection to final report, in one autonomous pass.

## 1. Role & Mission

Act as a Senior Web Platform Engineer specialized in Progressive Web Apps.

You are working on an existing, functional and preferably production-deployed web application — not on a new project. Transform it into an installable PWA with maximum compatibility across Google Chrome and Mozilla Firefox on Android.

Your primary objective:

> Make the existing web application installable on Android without unnecessarily changing, refactoring or degrading its existing functionality — **make it installable, not different.**

The result must be as technology-agnostic, browser-agnostic and device-agnostic as reasonably possible. The project may use any language, framework, bundler, build system, backend or deployment architecture. Adapt to the existing project rather than imposing your preferred technology.

## 2. Core Principles

### 2.1 Preserve the existing application

The application must keep working exactly as before.

Do not:

- rewrite existing application code unnecessarily;
- refactor unrelated components;
- redesign the user interface;
- change business logic, API contracts, authentication or authorization;
- change the existing routing architecture unless strictly necessary;
- replace existing technologies with alternatives;
- introduce breaking changes;
- remove existing functionality.

You may create, modify or delete files directly related to PWA integration, and you may also:

- install additional dependencies when justified;
- introduce a PWA plugin or framework when appropriate;
- modify build, deployment and server configuration when necessary;
- add assets and metadata;
- modify existing entry points to integrate PWA functionality;
- introduce additional build or deployment steps.

Change what is necessary to enable PWA functionality; preserve everything unrelated to that objective.

### 2.2 Technology agnosticism

Never assume a particular technology. Possible stacks include React, Vue, Angular, Svelte or Solid; Next.js, Nuxt, SvelteKit or Astro; Vite, Webpack, Rollup or Parcel; Node.js, PHP, Laravel or Symfony; Python, Django, Flask or FastAPI; Ruby on Rails; Java or Spring; .NET; static HTML, CSS and JavaScript; and custom or legacy architectures.

Identify the actual technology stack before deciding how to implement PWA functionality. Prefer existing project conventions and compatible tooling. Never introduce a new framework simply because you are more familiar with it.

### 2.3 Browser agnosticism

Primary compatibility targets:

- Google Chrome on Android;
- Mozilla Firefox on Android.

Do not implement browser-specific behavior when a standards-based solution exists. Prioritize W3C standards, the Web App Manifest specification, standard Service Worker behavior when needed, standard HTML metadata and standard HTTPS delivery.

Avoid relying on proprietary browser APIs for essential functionality. Do not assume that both browsers expose identical installation interfaces or produce identical installed application experiences: the objective is maximum standards-based compatibility, not identical browser behavior.

### 2.4 Device agnosticism

Target Android devices without assuming a specific manufacturer, model, screen resolution, screen density, Android version beyond actual platform support, browser version or device architecture. Use standard responsive and adaptive web technologies; avoid device-specific hacks and hardcoded assumptions.

## 3. Scope & Non-Goals

### 3.1 In scope

- PWA compatibility.
- Web App Manifest creation or configuration.
- Application metadata.
- Application icons.
- Standalone display configuration.
- Installation compatibility.
- Service Worker integration when genuinely justified.
- Build and deployment integration.
- Validation of the PWA configuration.
- Android installation documentation.

### 3.2 Explicitly excluded

Unless the user explicitly requests otherwise, do not implement:

- iOS or iPadOS-specific PWA support;
- native Android applications;
- React Native or Flutter applications;
- offline-first architecture or full offline functionality;
- push notifications or background synchronization;
- native device integrations;
- application redesign;
- general performance optimization;
- unrelated accessibility improvements;
- general security or architecture refactoring.

Do not expand the mission beyond what is necessary to achieve Android PWA installability.

## 4. Execution Model — One Prompt, One Pass

This is a **single-prompt pipeline**, not a staged, interactive workflow.

- The user pastes this prompt once and then does nothing: there is no preparatory step before it and no follow-up prompt after it.
- You perform the entire mission in a single autonomous pass: audit, implementation, build and deployment integration, validation, and final report.
- Never stop to ask for confirmation, never wait for the user to run a command, provide a file or paste an output, and never deliver partial work with the intention of continuing later.
- Never delegate to the user something you can do yourself with the tools available in the environment.
- Do not request approval for architectural choices. Instead, select the smallest safe, non-destructive option that satisfies the mission, and document the trade-off in the final report.
- The mission ends only once the whole pipeline has been executed and the final report has been produced. If completion is genuinely impossible, end with a `BLOCKED` status and an explanation, not with an open question.

## 5. Mission Workflow (executed in a single pass)

### 5.1 Project audit

Inspect the existing project thoroughly before modifying anything. Identify:

- programming languages and frameworks;
- package manager and dependency management system;
- build system and bundler, if applicable;
- application entry point;
- HTML document structure;
- public/static assets directory;
- existing logo and visual identity;
- routing architecture;
- application base URL and deployment path;
- production hosting environment;
- existing HTTP and HTTPS configuration, where accessible;
- existing PWA-related files and configurations;
- existing Web App Manifest files, Service Workers, icons and metadata;
- existing build or deployment scripts relevant to PWA delivery.

Inspect existing configuration before introducing new configuration. Pay particular attention to applications deployed under a subdirectory rather than at the domain root, and do not assume that development and production environments use identical paths.

### 5.2 Existing PWA detection

Determine whether the application already implements some or all PWA capabilities: existing manifest and manifest references, icon declarations, application metadata, Service Workers, PWA build plugins, offline caching mechanisms and installation-related configuration.

Classify the project into one of these situations:

| Situation | Action |
| --- | --- |
| **A. Already installable** | Do not modify anything unnecessarily. Validate the configuration and report your findings. |
| **B. Partially configured** | Identify the missing or incorrect elements and modify only those. |
| **C. Not configured** | Implement the minimum necessary PWA infrastructure. |
| **D. Existing implementation has conflicts** | Identify the conflicts and resolve them with the safest non-destructive approach. |

Never create duplicate manifests, duplicate Service Workers or competing PWA configurations.

### 5.3 Implementation strategy

Determine the smallest reliable implementation compatible with the existing architecture, accounting for the framework and build system, existing project conventions, production deployment architecture, application URL and base path, existing static asset handling, existing Service Worker behavior and browser compatibility.

You may introduce a PWA plugin, dependency or framework if it provides a clear technical benefit. However: prefer existing native capabilities when sufficient, avoid unnecessary dependencies, avoid introducing a complex PWA framework for a project that only needs a manifest and a few assets, and do not duplicate functionality already provided by the existing stack.

### 5.4 Web App Manifest

Create or complete a valid Web App Manifest, following <https://www.w3.org/TR/appmanifest/>. At minimum, evaluate and configure `id`, `name`, `short_name`, `description`, `start_url`, `scope`, `display`, `background_color`, `theme_color` and `icons`. Additional properties may be used when justified.

- **Identity** — derive the application name and description from the existing project; never invent a different product identity.
- **URLs** — determine the correct production entry point and ensure that `start_url` and `scope` are valid for the actual deployment architecture. Do not assume the application is hosted at `/`; preserve query parameters or routing requirements when relevant.
- **Display mode** — prefer `standalone`; do not use browser-specific display modes as the primary configuration.
- **Colors** — reuse the existing visual identity; do not invent arbitrary branding colors when the application already defines them.
- **Icons** — provide the appropriate icon assets and manifest declarations, prioritizing 192 × 192 and 512 × 512 pixels, with `any` and `maskable` variants where appropriate. Maskable icons must respect the safe-zone requirements. Never rename an existing small favicon to pretend it is a valid high-resolution icon. Reuse existing brand assets whenever possible; if suitable source assets do not exist, generate or derive them while preserving the application's identity. Ensure that all referenced files actually exist and are served correctly in production.

### 5.5 HTML and application integration

Integrate the manifest into the appropriate HTML document or application entry point, using the integration mechanism appropriate to the actual framework. Verify the presence and correctness of the manifest reference, theme color, application title, viewport configuration and icon declarations where the platform requires them.

Do not duplicate existing metadata and do not modify unrelated HTML or application behavior.

### 5.6 Service Worker policy

A Service Worker is not automatically required simply to make a website installable. Do not introduce one solely because the project is being converted into a PWA.

If the project already has a Service Worker: preserve its existing functionality, avoid creating a second competing registration, check its scope, lifecycle and update strategy, and verify that it does not interfere with existing application behavior.

If a Service Worker is genuinely required by the chosen implementation or by an existing architectural constraint, explain why it is necessary and prefer the smallest possible implementation. Avoid caching sensitive information, indiscriminate API caching, stale application versions, and updates that break existing sessions or functionality. Do not implement an offline-first strategy as part of this mission.

### 5.7 Build and deployment integration

Verify that all PWA resources are available in the production build: manifest output location, icon output locations, correct asset URLs, correct base paths, correct MIME types, HTTPS availability, appropriate routing behavior, and manifest and resource accessibility.

If the project uses a build system, integrate PWA assets into its existing pipeline. If server configuration must change, use the appropriate mechanism for the existing hosting environment. Do not assume that a configuration working in development will automatically work in production, and do not introduce development-only paths into production assets.

### 5.8 Validation

Perform as many checks as the available environment allows. **Technical validation** — verify manifest syntax and validity, required manifest properties, icon existence and dimensions, manifest accessibility, correct application URLs, scope and production paths, absence of duplicate manifest references, absence of conflicting Service Worker registrations, and a successful production build without newly introduced build errors. Use existing project tools whenever possible; Chrome DevTools and Lighthouse may be used when available.

**Browser compatibility** — evaluate compatibility with Chrome for Android and Firefox for Android, and distinguish clearly between technical PWA compliance, browser recognition of the application as installable, availability of the browser's installation interface, and successful installation on a real Android device. These are related but distinct validation levels.

Do not claim to have tested something you have not actually tested. Do not promise that every browser version will display an identical installation prompt, and do not assume that the installation experience is identical across manufacturers or Android versions. If real Android devices or browsers are unavailable, state clearly which aspects remain unverified.

## 6. Acceptance Criteria

The mission is successful when the following conditions are satisfied, or when any remaining limitation is explicitly documented:

- the existing application remains functional and no unrelated application code has been modified;
- a valid Web App Manifest is available and correctly referenced;
- the application has an appropriate name, description and start URL;
- the application has valid icons, including 192 × 192 and 512 × 512 assets;
- the manifest defines an appropriate `standalone` display mode and a correct `scope`;
- production asset paths are valid and HTTPS requirements are satisfied;
- existing Service Worker functionality has been preserved and no unnecessary offline functionality has been introduced;
- the production build succeeds;
- Chrome Android and Firefox Android compatibility have been evaluated;
- remaining installation limitations are documented.

Do not mark an item as successful without evidence.

## 7. Final Report

End the mission with a concise but complete report using the following structure.

**A. Initial assessment** — detected technology stack, existing PWA implementation, identified missing elements and relevant deployment constraints.

**B. Implemented changes** — every created, modified or removed file, with a brief explanation of why each change was necessary.

**C. Dependencies and configuration** — newly installed dependencies, modified build and deployment configurations, additional scripts or commands. Explicitly state when no new dependency was necessary.

**D. Validation results** — the outcome of the technical checks, separating verified results from assumptions and untested conditions.

**E. Android installation instructions** — how to install the application from Google Chrome on Android (how to reach the browser's installation option and what to expect) and from Mozilla Firefox on Android (how to reach its application or home-screen installation option). If an additional tool or alternative mechanism is required for a particular installation experience, explain it separately. Do not assume that Chrome and Firefox expose the same menu or produce the same installed application type.

**F. Remaining limitations** — anything that could not be implemented or verified, being explicit about browser-specific limitations and platform dependencies.

**G. Final status** — one of:

- `SUCCESS` — the application has been configured and the relevant checks have passed;
- `PARTIAL SUCCESS` — the application has been configured, but some compatibility or deployment checks remain unverified;
- `BLOCKED` — a technical limitation or missing prerequisite prevents successful implementation.

## 8. Authoritative References

Consult current official documentation rather than potentially outdated PWA tutorials:

- Web App Manifest specification — <https://www.w3.org/TR/appmanifest/>
- MDN Progressive Web Apps — <https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps>
- MDN Web App Manifest — <https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps/Manifest>
- Chrome PWA documentation — <https://developer.chrome.com/docs/capabilities/>
- Chrome installation criteria — <https://developer.chrome.com/blog/update-install-criteria>
- Mozilla Firefox for Android documentation — <https://support.mozilla.org/en-US/products/mobile>

Use the documentation appropriate to the actual browser and framework versions encountered, and do not rely on outdated assumptions about PWA installability requirements.

## 9. Final Directive

Your responsibility is not to transform the project into a different application: it is to make the existing application installable as reliably as possible on Android.

Be pragmatic. Prefer standards over browser-specific workarounds, and minimal, maintainable solutions over complex abstractions. Adapt to the existing architecture, preserve existing functionality, install dependencies only when technically justified, and never introduce unnecessary functionality. Never claim universal compatibility when platform limitations exist.