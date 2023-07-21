

1. Set API key in your .env file:
```
ELEVEN_LABS_API_KEY=<api key>
```
</details>

## 💿 Installation via Python
- **Step 1**. Clone the repo
   ```sh
   git clone https://github.com/Shaunwei/RealChar.git && cd RealChar
    ```
- **Step 2**. Install requirements
    - Install [portaudio](https://people.csail.mit.edu/hubert/pyaudio/) and [ffmpeg](https://ffmpeg.org/download.html) for audio
    ```sh
    # for mac
    brew install portaudio
    brew install ffmpeg
    ```
    ```sh
    # for ubuntu
    sudo apt update
    sudo apt install portaudio19-dev
    sudo apt install ffmpeg
    ```
    - Then install all python requirements
    ```sh
    pip install -r requirements.txt
    ```
- **Step 3**. Create an empty [sqlite](https://www.sqlite.org/index.html) database if you have not done so before
    ```sh
    sqlite3 test.db "VACUUM;"
    ```
- **Step 4**. Run db upgrade
    ```sh
    alembic upgrade head
    ```
- **Step 5**. Setup `.env`: update API keys and select module
   ```sh
   cp .env.example .env
   ```
- **Step 6**. Run server with `cli.py` or use uvicorn directly
    ```sh
    python cli.py run-uvicorn
    # or
    uvicorn realtime_ai_character.main:app
    ```
- **Step 7**. Run client:
    - Use **GPT4** for better conversation and **Wear headphone** for best audio(avoid echo)
    - There are two ways to access the web client:
        - **Option 1**: Open your web browser and navigate to http://localhost:8000 (NOT 0.0.0.0:8000)
        - **Option 2**: Running the client in React.
            ```sh
            cd client/web
            npm start
            ```
            After running these commands, a local development server will start, and your default web browser will open a new tab/window pointing to this server (usually http://localhost:3000).
    - (Optional) Terminal client: Run the following command in your terminal
    ```sh
    python client/cli.py
    ```
    - (Optional) mobile client: open `client/mobile/ios/rac/rac.xcodeproj/project.pbxproj` in Xcode and run the app
- **Step 8**. Select one character to talk to, then start talking


## (Optional) 📀 Installation via Docker
<details><summary>👇click me</summary>

1. Docker image: you can use our docker image directly
    ```sh
    docker pull shaunly/real_char:latest
    ```
    (Or you want build yourself) Build docker image
    ```sh
    python cli.py docker-build
    ```
    If you have issues with docker (especially on a non-Linux machine), please refer to https://docs.docker.com/get-docker/ (installation) and https://docs.docker.com/desktop/troubleshoot/overview/ (troubleshooting).
2. Run docker image with `.env` file
    ```sh
    python cli.py docker-run
    ```

3. Go to http://localhost:8000 (NOT 0.0.0.0:8000) to start talking or use terminal    client
    ```sh
    python client/cli.py
    ```

</details>

<br/>

## 🆕! LangSmith integration
<details><summary>👇click me</summary>

If you have access to LangSmith, you can edit these environment variables to enable:
```
LANGCHAIN_TRACING_V2=false # default off
LANGCHAIN_ENDPOINT=https://api.smith.langchain.com
LANGCHAIN_API_KEY=YOUR_LANGCHAIN_API_KEY
LANGCHAIN_PROJECT=YOUR_LANGCHAIN_PROJECT
```
And it should work out of the box.

</details>

<br/>
