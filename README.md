# automated-content-creation
### Description  
This endpoint is created as a prototype for automated content creation application. It takes an example image and creates a similar image by using Stable Diffusion. After that it combines some logos and text to form a programmatically generated content.


### Description

This endpoint is created as a prototype for automated content creation application. It takes an example image and creates a similar image by using Stable Diffusion. After that it combines some logos and text to form a programmatically generated content.

### Example Inputs & Output

#### Inputs

<img src='https://github.com/UkcaGreen/automated-content-creation-api/assets/42381853/1b1d86f2-56ad-49c7-b887-30ad22c66528' width='250'>
<img src='https://github.com/UkcaGreen/automated-content-creation-api/assets/42381853/4c7b0fda-2bdf-4f21-ac96-43b69e10a7ff' width='250'>

#### Output

<img src='https://github.com/UkcaGreen/automated-content-creation-api/assets/42381853/3103ee6d-9d77-430d-91d5-fd93e7b69c16' width='500'>

### How to run?
> Note: this application requires Stable Diffusion ([you can get it here](https://github.com/AUTOMATIC1111/stable-diffusion-webui)) running with `--api` flag. If stable diffusion is running at an address other than `http://127.0.0.1:7860`, please update `STABLE_DIFFUSION_URL` variable in `config.py`.

1. install requirements

`pip install -r requirements.txt`

2. start the application

`uvicorn main:app --reload`

3. navigate to application in your browser

Open `http://127.0.0.1:8000` at your browser, if you see `{"status": "ok"}``, installation is successful.

4. navigate to url endpoints
5. Navigate to `http://127.0.0.1:8000/docs` at your browser, you will see awailable endpoints there. You can use these endpoints by clicking `Try it out` buttons.

### Dev Logs

#### Handling Hex Codes

System also supports passing colors to use during both image and content creation. However Stable Diffusion was not that familiar with hex codes, rather it recognizes human readable color names. So hex codes are converted into human readable names by using `webcolors` library.

#### Constructing content

Content consists logo, image, text, and a button. In order to contruct the image, first each of the elements are generated separately and they gets poisitioned on a white canvas. All of these image manipulations 
