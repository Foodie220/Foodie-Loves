# Foodie-Loves
public/images/
public/images/churros.jpg
public/images/churros12.jpg
public/images/friedoreo.jpg
[
  { "name": "Churros", "price": 65, "image": "churros.jpg" },
  { "name": "Churros 12", "price": 120, "image": "churros12.jpg" },
  { "name": "Fried oreo", "price": 55, "image": "friedoreo.jpg" }
]
<div id="menu"></div>
<script>
fetch("/menu")
.then(res => res.json())
.then(menu => {
  const menuDiv = document.getElementById("menu");

  menu.forEach(item => {
    const itemDiv = document.createElement("div");
    itemDiv.style.marginBottom = "15px";

    itemDiv.innerHTML = `
      <img src="images/${item.image}" alt="${item.name}" 
           style="width: 100px; height: auto; border-radius: 8px;" />
      <h3>${item.name} — $${item.price}</h3>
      <button onclick="selectFood('${item.name}')">Select</button>
    `;

    menuDiv.appendChild(itemDiv);
  });
});

function selectFood(foodName) {
  document.getElementById("food").value = foodName;
}
</script>

<input type="hidden" id="food" required />
