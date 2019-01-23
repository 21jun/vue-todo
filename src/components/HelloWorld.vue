<template>
  <v-layout row>
    <v-flex xs12 sm6 offset-sm3>
      <v-card>
        <v-toolbar color="indigo" dark>
          <v-toolbar-side-icon></v-toolbar-side-icon>

          <v-toolbar-title>TODO</v-toolbar-title>

          <v-spacer></v-spacer>

          <v-btn icon @click="createItem(title)">
            <v-icon>ADD</v-icon>
          </v-btn>

          <v-btn icon @click="clearAll()">
            <v-icon>XX</v-icon>
          </v-btn>
        </v-toolbar>
        <v-list>
          <input type="text" class="form-control" placeholder="할일을 입력하세요" v-model="title" v-on:keyup.enter="createItem(title)">
          <v-list-tile
            v-for="(item,index) in items"
            :key="item.title"
            avatar
            @click="deleteItem(index)"
          >
            <v-list-tile-content>
              <v-list-tile-title v-text="item.title"></v-list-tile-title>
            </v-list-tile-content>
          </v-list-tile>
        </v-list>
      </v-card>
    </v-flex>
  </v-layout>
</template>
<script>
  export default {
    data () {
      return {
        title:"",
        items: [
          { title: '수업 참가' },
          { title: '집 가기' },
          { title: '밥 먹기' }
        ]
      }
    },
    methods:{
      deleteItem(i)
      {
        this.items.splice(i,1)
      },
      createItem(title)
      {
        if(title === "") return
        if(title != null){
          this.items.push({title:title});
          this.title = null
			  }
      },
      clearAll()
      {
        this.items=[];
      }
    }
  }
</script>