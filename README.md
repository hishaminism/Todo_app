var itemList = document.getElementById('item_list');
function addItem(element) {
    //creteing item element
    let item        = document.getElementById('item').value;
    let itemText    = document.createTextNode(item);
    //wrapping text within span
    let span        = document.createElement('span');
    span.appendChild(itemText);

    let itemLi      = document.createElement('li');
    itemLi.append(span);
    itemList.append(itemLi);

    //add delete button
    let delbtn         = document.createElement("button");
    delbtn.setAttribute('onclick','deleteItem(this)')
    delbtn.innerHTML   = "Delete";
    delbtn.type        = "submit";
    delbtn.name        = "delbtn";
    itemLi.appendChild(delbtn);

    //update btn
    let Updatebtn         = document.createElement("button");
    Updatebtn.setAttribute('onclick','updateItem(this)')
    Updatebtn.innerHTML   = "Update";
    Updatebtn.type        = "submit";
    Updatebtn.name        = "Updatebtn";
    itemLi.appendChild(Updatebtn);
}

function deleteItem(element) {
    if( confirm('Are you sure?') === true )
        element.parentNode.remove();
    
}

function updateItem(element) {
    let fChild      = element.parentNode.firstChild;
    let updatedText = prompt("Update item", fChild.textContent);
    element.parentNode.firstChild.textContent = updatedText;
}

function deleteAllItems() {
    if( confirm('Are you sure?') === true ) {
        const allItems = document.getElementById("item_list");
        allItems.innerHTML = '';
    }  
}
