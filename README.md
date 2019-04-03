

# Few points to consider by developers while writing react application 

1. Mandatory points to follow
2. Better to follow these as well

### Mandatory points to follow: 
1. Strictly, **Don’t mutate the object which is part of state**. If we Mutate, we are disturbing the react lifecycle. 
2. Use **only Unique keys while rendering the lists**(unique in the sense, unique among that particular list and should be same after every rerender, may be some id’s,..), If we don’t give unique values to the keys then you are not using the main feature of react for which facebook has created this library. 
3. which life cycle method is better to use for api calls? **ComponentDidMount**, Avoiding api calls in constructor or ComponentWillMount will reduce unnecessary re-render calls. 

4. Flux listener’s should be used appropriately, Using unwanted listeners will trigger the Updation lifecycle, Even Though React is intelligent enough not to change the dom, But we are executing too much javascript and creating Virtual doms and triggering the diffing algorithm. 
5. Proper use of Stateful, Stateless and PureComponents. Limit the use of Stateful Component and let’s not misuse the PureComponents. We should not neglect splitting of components, It’s plays a major role in performance, It will described in detail in the attached document.
 

6. Misuse of State variables. Including all the variables as part of state should not be done, Include only those variables in state that should be rendered, any other variables should never be part of state, It should be part of class variables or local scope to a function. 

7. Avoid inline CSS, This is the basic thing of all which we should not encourage. 


**If we couldn’t follow the above things, then we are misusing the react library. It’s like we are continuously hitting the tree without sharpening the axe.**


### Better to follow these as well
1. Using sprite images, This is a basic thing which we are still missing. Too many request to the server just for an icon will make the browser busy and wastage of infrastructure and troubling user’s bandwidth as well. 
 

2. Removing Unused imports, Even Though webpack doesn’t include them in the final bundle let’s import only those modules that are required and follow a pattern while importing. First import the external libraries then our generic components and then siblings or any other  components. 

3. Avoid binding the functions in render function. Use ES6 Arrow Keys or bind them in constructor. when you wan’t to pass parameters to the function, please curry the function and bind it. 

4. Use SetState carefully, For example you got some data from backend and you want to manipulate the data and show to the user. It’s better to manipulate the data first and then set it in the state, But mostly we are setting the state immediately while we get the data from the backend and then applying modification  on the state which triggers the updation lifecycle too much(Can be easily avoided).

5. Reducing the updation lifecycles. If we need 6 api calls to render a page, Then it’s better we update the state only after the mandatory api calls return the data. We can use axios or any other comfortable library to do the parallel calls and update the state when mandatory data is returned. 

6. Use Debounce/Throtlle to avoid unnecessery callback(Please use these functions especially in autosuggestions and scrolling, if not used you can't have smooth flow). Libraries like React virtualized help to create less no of Dom nodes when rendering huge no of nodes.

7. It’s better to avoid copying the props to state with out proper purpose. Instead you can directly use the props where required and use ComponentWillRecevieProps to find out the changes. 

8. Please use react-perf tool to calculate the performance of the project. There are lot more other tools like lightbox, profiling, memory,...provided by Google chrome developer tools. While calculating the performance please use an incognitive  mode so that other addons installed on browser won't effect the performance while calculating it.  



### Few honourable mentions 

1. Please use lodash and immutable.js. There are good functionalities provided by lodash, for ex to checking the values of objects when the chain is too long. we are using endless && operator which hampers the readability, instead we can use lodash or write our own lib. 

2. please use  eslint-plugin-react 
3. Code splitting(resource splitting and on demand code splitting)
4. CommonsChunkPlugin→  you can extract common code (such as all external libraries) into a “chunk” file of its own. 
5. Using ExtractTextWebpackPlugin, you can extract all CSS code into a separate CSS file.
This kind of splitting will help in two ways. It helps the browser to cache those less frequently changing resources. It will also help the browser to take advantage of parallel downloading to potentially reduce the load time.

Our code should be our documentation. :)
