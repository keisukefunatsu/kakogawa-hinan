<template>
    <section class="container">
        <h1>避難所マップ</h1>
        <div id="map" style="width:100%;height: 700px">
            <no-ssr>
                <l-map ref="map" :zoom=16 :center="center">
                    <l-tile-layer url="http://{s}.tile.osm.org/{z}/{x}/{y}.png"></l-tile-layer>>
                    <!-- <marker-popup :position="center" :text="text" :title="title"></marker-popup> -->
                        <l-marker v-for="(info, index) in hinan" :key="index" :lat-lng="[info['lat'], info['lng']]">
                            <l-popup>
                                <h2>{{info['名称']}}</h2>
                                <table class="table is-bordered">
                                    <tr>
                                        <th>電話番号</th>
                                        <th>収容可(屋内)</th>
                                        <th>収容可(屋外)</th>
                                    </tr>
                                    <tr>
                                        <td>{{info['電話番号']}}</td>
                                        <td>{{info['収容人数_屋内']}}人</td>
                                        <td>{{info['収容人数_屋外']}}人</td>
                                    </tr>  
                                </table>
                                <table class="table is-bordered">
                                    <h2>対応可能災害</h2>
                                    <tr>                                    <tr>
                                        <th>洪水</th>
                                        <th>土砂災害</th>
                                        <th>高潮</th>
                                        <th>地震</th>
                                        <th>津波</th>
                                        <th>大規模火災</th>
                                    </tr>
                                    <tr>
                                        <td>{{info['避難場所指定_洪水']}}</td>
                                        <td>{{info['避難場所指定_土砂災害']}}</td>
                                        <td>{{info['避難場所指定_高潮']}}</td>
                                        <td>{{info['避難場所指定_地震']}}</td>
                                        <td>{{info['避難場所指定_津波']}}</td>
                                        <td>{{info['避難場所指定_大規模火災']}}</td>
                                    </tr>   
                                </table>
                                <h2>備蓄物資</h2>
                                <p>
                                    {{info['備蓄物資']}}
                                </p>
                            </l-popup>
                        </l-marker>
                </l-map>
            </no-ssr>
        </div>
    </section>
</template>

<script>
import { LMap, LTileLayer, LMarker, LIconDefault } from "nuxt-leaflet";
// import MarkerPopup from "~/components/MarkerPopup";
import hinan from "~/assets/disaster/12_shiteikinkyuhinanbasyokenshiteihinanjyo.json";
export default {
  //   components: { MarkerPopup },
  data() {
    return {
      hinan: hinan,
      map: null,
      center: [34.757175, 134.841167],
      text: "hello",
      title: "title"
    };
  },
  methods: {},
  created() {}
};
</script>
<style>
#map {
  width: 500px;
  height: 500px;
}
</style>
