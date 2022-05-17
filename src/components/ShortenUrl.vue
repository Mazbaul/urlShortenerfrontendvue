<template>
<div class="content">
        <div class="animated fadeIn">
            <div class="row">
                <div class="col-lg-12">
                    <div class="card">
                            <div>
                                <div class="card-body">
                                    <div class="row">
                                        <div class="col-12 col-md-10 offset-md-1">
                                                <div class="row form-group">
                                                    <div class="col-9" style="padding-right: 0;">
                                                      <label for="amount">URL:</label>
                                                        <input type="text" name="url" class="form-control" v-model="url">
                                                    </div>

                                                    <div class="col-3" style="padding-top: 2%;">
                                                        <button type="submit" @click="this.sendurl(url)" class="btn btn-info pull-right" style="width:100%;"><i class="fa fa-search"></i>&nbsp; Send</button>
                                                    </div>
                                                </div>
                                        </div>
                                    </div>
                                </div>
                            </div>
                    </div> <!-- .card -->
                    <div class="card">
                            <div>
                                <div class="card-body">
                                    <div class="row">
                                        <div class="col-12 col-md-10 offset-md-1">
                                          <table id="bootstrap-data-table" class="table table-striped table-bordered dataTable no-footer" role="grid" aria-describedby="bootstrap-data-table_info">
                                        <thead>
                                            <tr role="row">
                                                <th class="text-center" style="width: 6%;">SL</th>
                                                <th class="text-center" style="width: 20%;">Original URL</th>
                                                <th class="text-center" style="width: 20%;">Shorten URl</th>

                                            </tr>
                                        </thead>
                                        <tbody>

                                            <tr role="row" class="">
                                                <td class="text-center"></td>
                                                <td class="text-center"></td>
                                                <td></td>

                                            </tr>

                                        </tbody>
                                    </table>
                                        </div>
                                    </div>
                                </div>
                            </div>
                    </div> <!-- .card -->
                </div><!--/.col-->
            </div>
        </div><!-- .animated -->
    </div><!-- .content -->
</template>

    <script >
    export default {
      name: "ShortenUrl",
      data() {
        return {
           url:'',
           allData:{},

        };
      },
      methods:{
        getData:function(){
          const th = this
          this.axios.get('http://127.0.0.1:8000/api/all-shorten-url').then(response => (
            th.allData = response.data

          ))
        },
        sendurl:function(url){
          const th = this
          this.axios.post('http://127.0.0.1:8000/api/generate-shorten-url?url='+url).then(response => (
            th.url = '',
            console.log(response.data)

          ))
        }
      },
      mounted(){
        this.getData();
       }
    }
    </script>
    <style scoped>

    </style>
