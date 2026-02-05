# Aplikacja Społecznościowa

Aplikacja społecznościowa składająca się z frontendu, backendu oraz bazy danych, zarządzanych za pomocą Docker Compose.

## Technologie

Projekt składa się z trzech głównych modułów:

### Backend
* **Język:** Java 21
* **Framework:** Spring Boot 3
* **Baza danych:** PostgreSQL
* **Bezpieczeństwo:** Spring Security + JWT (JSON Web Tokens)
* **Build Tool:** Maven

### Frontend
* **Framework:** Angular (v17+)
* **Serwer produkcyjny:** Nginx (Alpine)
* **Build Tool:** NPM

### Wirtualizacja
* **Docker** - konteneryzacja aplikacji
* **Docker Compose** - orkiestracja wielu kontenerów (baza danych, backend, frontend)

## Główne Funkcjonalności

Aplikacja jest w trakcie rozwoju. Aktualnie dostępne są następujące funkcjonalności:

* **Uwierzytelnianie:** Rejestracja, logowanie, obsługa tokenów JWT.
* **Posty:** Możliwość dodawania nowych postów.
* **Profil Użytkownika:** Edycja informacji na profilu.
* **Interakcje:**
    * Dodawanie komentarzy do postów.
    * System polubień (lajków).

## Struktura projektu

- `/frontend` - Kod źródłowy aplikacji klienckiej.
- `/backend` - Kod źródłowy API.
- `.env_template` - Przykładowy plik konfiguracyjny zmiennych środowiskowych.
- `docker-compose.yml` - Plik konfiguracyjny orkiestracji kontenerów.

## Instalacja i Uruchomienie

Projekt jest w pełni skonfigurowany do uruchomienia przy użyciu Docker Compose.

### Wymagania wstępne
* Docker 
* Docker compose

1.  **Sklonuj repozytorium:**
    ```bash
    git clone https://github.com/adriansiwek333/social-media-platform.git
    cd social-media-platform
    ```

2.  **Konfiguracja zmiennych środowiskowych:**
    Utwórz plik `.env` w głównym katalogu projektu, bazując na dostarczonym szablonie.

    ```bash
    cp .env_template .env
    ```

    ```properties
    # .env
    POSTGRES_DB=your_db_name
    POSTGRES_USER=your_db_user
    POSTGRES_PASSWORD=your_db_password

    DB_USERNAME=your_db_user
    DB_PASSWORD=your_db_password
    DB_URL=jdbc:postgresql://db:5432/your_db_name
    JWT_SECRET=E12V6H/q4mc3gRBqYOTKWpOtif7bJKnnGpfEwpDbpfk=
    ```

3.  **Uruchomienie aplikacji:**
    W terminalu wykonaj polecenie:
    ```bash
    docker-compose up --build
    ```

## Dostęp do aplikacji

Po poprawnym uruchomieniu kontenerów, usługi będą dostępne pod następującymi adresami:

| Usługa | URL / Port | Opis |
| :--- | :--- | :--- |
| **Frontend** | `http://localhost:80` | Główny interfejs aplikacji (Angular serwowany przez Nginx). |
| **Backend API** | `http://localhost:8080` | API Spring Boot. |
| **Baza Danych** | `localhost:5433` | Dostęp do PostgreSQL z zewnątrz. Wewnątrz Dockera działa na porcie 5432. |

## Struktura Projektu

```text
social-media-platform/
├── backend/            # Kod źródłowy API (Java/Spring Boot)
│   ├── src/
│   └── Dockerfile      # Konfiguracja obrazu backendu
├── frontend/           # Kod źródłowy interfejsu (Angular)
│   ├── src/
│   ├── nginx.conf      # Konfiguracja serwera WWW
│   └── Dockerfile      # Konfiguracja obrazu frontendu
├── docker-compose.yml  # Orkiestracja usług
└── .env_template       # Szablon zmiennych środowiskowych
