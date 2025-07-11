# Electronic Campus of Igor Sikorsky Kyiv Polytechnic Institute

[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](http://makeapullrequest.com)
[![Docker Image Version (latest by date)](https://img.shields.io/docker/v/kpiua/ecampus.kpi.ua)](https://hub.docker.com/r/kpiua/ecampus.kpi.ua)
[![GitHub license](https://img.shields.io/github/license/kpi-ua/ecampus.kpi.ua.svg)](https://github.com/kpi-ua/ecampus.kpi.ua/blob/master/LICENSE)
[![GitHub contributors](https://img.shields.io/github/contributors/kpi-ua/ecampus.kpi.ua.svg)](https://GitHub.com/kpi-ua/ecampus.kpi.ua/graphs/contributors/)

The information system "Electronic Campus of Igor Sikorsky Kyiv Polytechnic Institute" is an automated system supporting educational process informatization. It provides digital communication tools for students, faculty, and department heads, enhancing educational quality through modern technology.

## Environment variables

- CAMPUS_API_BASE_PATH - Campus API URL. Dev value: `https://dev-api.campus.cloud.kpi.ua`
- MAIN_COOKIE_DOMAIN - Main site cookie domain name (for ecampus-token). Dev value: `localhost`
- ROOT_COOKIE_DOMAIN - Root site cookie domain name (for SID). Dev value: `localhost`
- NEXT_PUBLIC_RECAPTCHA_KEY - Google ReCaptcha v3 public key. Dev value: `6LeMy30qAAAAAIC6KUhNfReP-Us5wkrkp3FLfOgl`

## Run project locally

```shell
npm i
npm run dev
```

## Build project for production

```shell
npm run build
```

## Run production build

```shell
npm run start
```

### Run storybook

```shell
npm run storybook
```

## [Docker](https://hub.docker.com/r/kpiua/ecampus.kpi.ua)

### Build container

```shell
docker build ./ --file ./Dockerfile --tag kpiua/ecampus.kpi.ua:latest
```

### Run

#### Run with default settings

```shell
docker run --rm -it -p 3000:3000/tcp kpiua/ecampus.kpi.ua:latest
```

#### Run with custom settings

```shell
 docker run --rm -it -e CAMPUS_API_BASE_PATH=https://dev-api.campus.cloud.kpi.ua -p 80:80/tcp kpiua/ecampus.kpi.ua:latest
```

or

```shell
docker run --rm -it \
  -e CAMPUS_API_BASE_PATH=https://dev-api.campus.cloud.kpi.ua \
  -e MAIN_COOKIE_DOMAIN=localhost \
  -e ROOT_COOKIE_DOMAIN=localhost \
  -e NEXT_PUBLIC_RECAPTCHA_KEY=6LeMy30qAAAAAIC6KUhNfReP-Us5wkrkp3FLfOgl \
  -p 3000:3000/tcp kpiua/ecampus.kpi.ua:latest
```

## Adding translations

Translations are located in `en.json` and `uk.json` files inside `/src/messages/` folder for English and ukrainian languages accordingly. When adding a new translations, follow the same naming convention as in these files: property naming is in `kebab-case`.

You can use following tags in translations, they are defined globally and will be transformed automatically:

- `<p>` — will transform to `<Paragraph>` component.
- `<br></br>` — will transform into `<br/>`.
- `<h1> ... <h6>` — will transform into `<Heading1> ... <Heading6>`.
- `<ul>` — will transform into `<UlList>`.
- `<li>` — will transform into `<li>`.
- `<tel>` — will transform into a link with provided telephone number.
- `<email>` — will transform into a link with provided email address.

For more information see `src/i18n/request.tsx` file.
