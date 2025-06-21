// Calculate income resources
var fa = 0,
agyag = 0,
vas = 0,
sitter = "";
if (game_data.player.sitter != "0") {
sitter = "t=" + game_data.player.id + "&";
}
function createHead() {
$("#production_table").find("tr:eq(0)").append("<th>Fa</th>");
$("#production_table").find("tr:eq(0)").append("<th>Agyag</th>");
$("#production_table").find("tr:eq(0)").append("<th>Vas</th>");
}

createHead();
var link = "https://" + window.location.host + "/game.php?" + sitter + "village=";
function getPage(id, pages) {
if (id < pages) {
var url = link + $(`#production_table .quickedit-vn:eq(${id})`).attr("data-id");
$.ajax({
type: 'GET',
url: url,
dataType: "html",
success: function(data) {
$("#show_prod strong", data).each(function(k,v) {
if (k == 0) {
classname = "fa";
} else if (k == 1) {
classname = "agyag";
} else {
classname = "vas";
}
$("#production_table").find(`tr:eq(${id+1})`).append(`<td class=${classname}>` + $(this).html() + `</td>`);
});
setTimeout(function() {
getPage(id + 1, pages);
}, 200);
}
});
} else {
sum()
}
}

getPage(0, totalPages());


function totalPages() {
return parseInt($("#production_table").find("th:eq(1)").text().match(/\d+/)[0]);
}

function numberWithCommas(x) {
var parts = x.toString().split(".");
parts[0] = parts[0].replace(/\B(?=(\d{3})+(?!\d))/g, ".");
return parts.join(".");
}

function sum() {
$(".fa").each(function(key,value) {
fa += parseInt($(value).text().replace(".",""));
});
$(".agyag").each(function(key,value) {
agyag += parseInt($(value).text().replace(".",""));
});
$(".vas").each(function(key,value) {
vas += parseInt($(value).text().replace(".",""));
});
console.log(fa, agyag, vas);

var prod = {
text: [`Total`,
`<br/>`,
`<br/>`,
`Wood: ${numberWithCommas(fa) + ", daily production: " + numberWithCommas(24 * fa)}`,
`<br/>`,
`Clay: ${numberWithCommas(agyag) + ", daily production: " + numberWithCommas(24 * agyag)}`,
`<br/>`,
`iron: ${numberWithCommas(vas) + ", daily production: " + numberWithCommas(24 * vas)}`].join('')
};
UI.SuccessMessage(prod.text,20000);
}
void(0);
