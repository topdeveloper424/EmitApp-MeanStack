# 1. Preparation heroku

Please signup on the heroku and signin on it and create new node app.

# 2. Preparation mlab and Setting other environments

It is mean stack project. So it needs mongodb. It is using mlab as a remote mongodb.<br>
If you create your own mlab account, you should change the remote mongodb url on `backend/lib/conf.ts` line 2 <br>
You can also change other envrionment variables (for example: `mail password`, `mail username` so on) on this file.
<br>
You can use google captcha with your own site_key. <br>
In that case you need to change the code in backend and frontend.
You can find the variables on the environment.ts for frontend `src/enviroment/environment(prod).ts`. <br>
You can find the vairables on the conf.ts for backend. `lib/conf.ts`.<br>

# 3. How to run this project in local
Please `npm install` for both of angular(frontend) and node(backend).<br>
And please input `ng serve` in the root directory of frontend and `npm run dev` in the root directory of backend.<br>
And navigate your browser and input following url `http://localhost:4200`.<br>
That's all<br>

# 4. How to deploy this project to Heroku

## 4.1. Angular build
Angular project should be built first.
The command is like this(on the directory of the angular project). `npm install` `ng build --prod`.<br>
After that, the compiled source will be automatically nested on the pubilc directory of the node server.<br>

## 4.2. Node build

This node server was made by Type script(`.ts`).<br>
So in order to deploy it to the Heroku, It should be compiled.<br>
The command is like this (on the directory of the node project). `npm install` `npm run build`.<br>
After that, It will be compiled and make the `dist` directory on the root directory of node server.<br>
(It can be run on localhost:8080 locally)<br>

## 4.3. Deploy on Heroku

Please install Heroku CLI and GIT on your PC.<br>
And Please input following commands (on your local) to deploy the node sever into your heroku.<br>
`git init`<br>
`heroku create`<br>
`git add .`<br>
`git commit -m 'your commit'`<br>
`git push heroku master`<br>
`heroku ps:scale web=1`<br>
`heroku open`<br>

# 5. How to merge with Item Parts
## 5.1 Angular Part
### 5.1.1 Please copy the Item Directory (`frontend/src/app/views/item`) of emet-meanstack repo and paste it current Item Directory
### 5.1.2 Change the route when user login based on user role(admin or user)
 You can change it just like (`frontend/src/app/views/sessions/signin/signin.component.ts` 99 ~ 101 line) of emet-meanstack repo<br>
`...`<br>
`if (res.role === 1) { // admin`<br>
    `this.router.navigate(['/user/list']);`<br>
`} else { // user`<br>
    `this.router.navigate(['/item/list']);`<br>
`} `<br>
##5.2 Node Part
### 5.2.1 Please copy the itemController (`backend/lib/controllers/itemController.ts`) of emet-meanstack repo and replace it with the one on the current controllers directory.
