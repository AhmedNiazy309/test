<template>
  <div class="container">
    <nuxt-link to="pla">Ahmed</nuxt-link>
    <table id="example" class="display" style="width: 100%">
      <thead>
        <tr>
          <th>Name</th>
          <th>Position</th>
          <th>Office</th>
          <th>Age</th>
          <th>Start date</th>
          <th>Salary</th>
          <th>pla</th>
        </tr>
      </thead>
    </table>
  </div>
</template>
<script>
if (process.browser){
$(document).ready(function(){
      // console.log(123456);

      //$('a').on('click', 'editor_remove', function (e) {
        $("button").click(function(){
        e.preventDefault();
 
 // $(this).closest('tr').remove();
        console.log(123456);
} );

});
}
export default {
  name: "index",

  data() {
    return {
      dataTable: null,
      externalLoaded: false,
    };
  },
  mounted() {
    console.log("table mounted");
    if (this.dataTable === null) {
      this.onScriptLoaded();
    }
  },
  methods: {
    onScriptLoaded() {
      this.externalLoaded = true;
      console.log("script loaded");
      this.dataTable = $("#example").DataTable({
        processing: true,
        serverSide: true,
        ajax: "http://mohamedkhalid.brandup.ninja/api/v1/faculty/index",
        columns: [
          { data: "id" },
          { data: "name" },
          { data: "des" },
          { data: "image" },
          { data: "created_at" }, 
          { data: "updated_at" },
          {
            data: null,
            className: "center",
            defaultContent:
              '<button class="editor_remove">Remove</button>',
          },
        ],
      });
    },
  },
};
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont,
    "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
