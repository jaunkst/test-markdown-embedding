<script>
    
class Modal extends HTMLElement {
  constructor() {
    super();
    this.attachShadow({ mode: "open" });
    this.shadowRoot.innerHTML += "<style>button{background:#CCC;border:none; padding:10px 15px; border-radius:3px;}button:hover{background:#BBB;}button:active{background:#999;}</style>";
    this.shadowRoot.innerHTML += "<button>This button is a web component</button>";
  }

  connectedCallback() {
    this._modal = this.shadowRoot.querySelector(".modal");
    this.shadowRoot
      .querySelector("button")
      .addEventListener("click", this._showModal.bind(this));
  }
  disconnectedCallback() {
    this.shadowRoot
      .querySelector("button")
      .removeEventListener("click", this._showModal);
  }
  _showModal() {
    alert("My first web component");
  }
}
customElements.define("b-modal", Modal);

class Modala extends Modal {
  constructor() {
    super();
    this.shadowRoot.innerHTML +=
      "<style>button{background:green;}</style>";
  }
}

customElements.define("b-modala", Modala);

</script>


<b-modal>Button</b-modal>
<b-modala>Button</b-modala>
