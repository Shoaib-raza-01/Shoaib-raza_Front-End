Name - Md Shoaib Raza
Regn_No - 12017811


Answer1 - 

List is a React component used for an interactive UI design to display items in a more readable form placing them vertically / horizontally.
Here the component WrappedListComponent maps the item and create a SingleListItem and passes these props  :-

 'onClickHandler' -- function that handle the click functionality and change the background color of the text from red to green
 'text' -- it is the content that is to be set for the list to be displayed
 'index' -- it is the position of the item and it is being used by the onClickHandler function to find which text need to be colored
 'isSelected' .-- used to set the state and make null to clear the selection and make the background color to red

Here memo is used to improve the performance by skipping the rendering of a component if the props have not changed.






Answer 2 -

This code is having several error in it which needs to be addressed for the proper functioning of it.


Propblem-1 : In the SingleListItem onClickHandler={() => handleClick(index)} is having the error. It is not called with any argument
correction : Repalce that line with  onClickHandler={(event) => onClickHandler(index)} 
-----------------------------------OR----------------------------------either of the things can be done------------------------
Problem-2 :  The ‘onClickHandler’ prop is not being passed correctly in the ‘SingleListItem’ component,
Correction : It should be ‘onClick={onClickHandler}’ 


Problem-3 : In the ‘SingleListItem’ component, the ‘isSelected’ prop is having the error, it should have boolean value but object of was passed of useState hook .
Correction : It should be ‘isSelected={selectedIndex === index},   this ===(triple sign) comparison will returns boolean value.

Problem-4 : In the ‘WrappedListComponent’ component, the ‘PropTypes.array’ declaration for ‘items’ should be ‘PropTypes.arrayOf’ instead and 'shapeOf' should be changed to shape().
Correction : It should be ‘PropTypes.arrayOf(PropTypes.shape({ text: PropTypes.string.isRequired }))’.

Problem-5 : In the ‘WrappedListComponent’ component, the ‘useState’ hook is not being initialize with a default value The first argument to ‘useState’ should be the initial state value, and the second argument should be the state updater function.
Correction : It should be ‘const [selectedIndex, setSelectedIndex] = useState(null);’ null value is the initial value .
