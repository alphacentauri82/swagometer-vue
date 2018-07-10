<template>
  <section>
      <div class="container">
        <div class="row justify-content-md-center">
          <div class="col-xs-12">
            <h1><strong>SWAG-O-METER</strong></h1>
            <form @submit.prevent="obtenerRitmosustancia">
              <div class="form-group">
                <input type="text" class="form-control" v-model="name" value="name" id="name" required placeholder="Insert your name">
        
                <button type="submit" class="btn btn-primary btn-lg btn-block">Show me my swag!</button>
              </div>
            </form>
            <div>
              <ul class="list-group text-left">
                <li v-for="(item, index) in elements" :key="index" class="list-group-item">
                  <strong>Name: {{elements[index].name}}</strong> <br/>  
                  Swag: {{elements[index].swag}}
                  <div class="progress">
                    <div :class="`progress-bar progress-bar-striped progress-bar-animated ${elements[index].classStyle}`" role="progressbar" :style="`width: ${elements[index].swag}%`" :aria-valuenow="`${elements[index].swag}`" :aria-valuemin="`${elements[index].swag}`" aria-valuemax="100"></div>
                  </div>
                </li>
              </ul>
            </div>
          </div>
        </div>
      </div>
  </section>
</template>

<script>
export default {
  name: 'Index',
  data: () => ({
      name: '',
      elements: [
        {
          name: 'Super Diana',
          swag: 100,
          classStyle: 'bg-success'
        }
      ]
    }
  ),
  methods: {
    obtenerRitmosustancia() {
      let swag = Math.floor(Math.random() * 100) + 1
      let classStyle = (swag > 75) ? 'bg-success' : (swag > 50) ? 'bg-info' : (swag > 25) ? 'bg-warning' : 'bg-danger'
      this.elements.push({
        name: this.name,
        swag: swag,
        classStyle: classStyle
      })
      this.name = ''
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  form{
    margin-top: 25px;
  }
</style>
