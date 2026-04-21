# DotNetSampleAPI

A small **ASP.NET Core 8** sample Web API you can copy patterns from or use as a starting point in other projects. It follows the default Visual Studio / `dotnet new webapi` style: **controllers**, **Swagger / OpenAPI**, and the classic **WeatherForecast** demo endpoint.

This repository is a fork of [deepak-chic/DotNetSampleAPI](https://github.com/deepak-chic/DotNetSampleAPI). Upstream copy: [github.com/deepak-chic/DotNetSampleAPI](https://github.com/deepak-chic/DotNetSampleAPI). This fork: [github.com/deepak-agarwal-rsystems/DotNetSampleAPI](https://github.com/deepak-agarwal-rsystems/DotNetSampleAPI).

## What is in this repo

| Area | Details |
|------|---------|
| **Runtime** | .NET 8 (`net8.0`) |
| **Project type** | ASP.NET Core Web API (`Microsoft.NET.Sdk.Web`) |
| **API explorer** | Swashbuckle.AspNetCore 6.5.0 — Swagger UI in Development |
| **Sample API** | `GET /weatherforecast` returns five random weather rows |
| **Globalization** | `InvariantGlobalization` is enabled in the project file |

## Prerequisites

- [.NET 8 SDK](https://dotnet.microsoft.com/download/dotnet/8.0)
- Optional: Visual Studio 2022, VS Code, or JetBrains Rider

## Run locally

From the repository root:

```bash
dotnet restore
dotnet run --project DotNetSampleAPI
```

With the default **https** profile (see `DotNetSampleAPI/Properties/launchSettings.json`), the app listens on:

- HTTPS: `https://localhost:7125`
- HTTP: `http://localhost:5205`

In **Development**, the pipeline enables Swagger UI. After starting the API, open **Swagger** at `/swagger` (the launch profiles set `launchUrl` to `swagger`).

## Try the API

- **Browser or REST client:** `GET https://localhost:7125/weatherforecast` (or `http://localhost:5205/weatherforecast` over HTTP).
- **Visual Studio / VS Code:** open `DotNetSampleAPI/DotNetSampleAPI.http` and run the included `GET` request (uses `http://localhost:5205` by default).

Response: JSON array of objects with `date`, `temperatureC`, `temperatureF`, and `summary`.

## Project layout

```text
DotNetSampleAPI.sln          # Solution file
DotNetSampleAPI/
  Controllers/
    WeatherForecastController.cs
  Properties/
    launchSettings.json      # Kestrel / IIS Express URLs and Swagger launch URL
  Program.cs                 # Minimal hosting: controllers, Swagger, HTTPS
  WeatherForecast.cs         # Sample DTO
  appsettings.json           # Default configuration
  appsettings.Development.json
  DotNetSampleAPI.csproj
  DotNetSampleAPI.http       # Sample HTTP requests for tooling
LICENSE.txt
```

## Configuration notes

- **HTTPS:** `UseHttpsRedirection()` is enabled; use the HTTPS URL or trust the dev certificate (`dotnet dev-certs https --trust` on Windows/macOS).
- **Authorization:** `UseAuthorization()` is registered; the sample controller does not use `[Authorize]` — add authentication when you extend the API.

## Build

```bash
dotnet build DotNetSampleAPI.sln -c Release
```

## License

See [LICENSE.txt](LICENSE.txt) in this repository.
