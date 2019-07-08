<template>
  <v-simple-table>
    <tbody>
      <tr v-for="(value, name) in textStyles" :key="name">
        <td>
          <div v-if="value.styles === null"></div>
          <div v-else-if="value.styles == {}">
            ...
          </div>
          <div v-else class="caption rai-data text--secondary text-xs-right">
            {{ value.font }}<br>{{ value.weight }}<br>{{ value.size }}
          </div>
        </td>
        <td :class="name" :ref="name" >
          {{ value.demo }}
        </td>
      </tr>
    </tbody>
  </v-simple-table>
</template>

<script>
export default {
    data: function() {
      return {
        textStyles: {
          "display-4": { styles: null, demo: "Heading 1", font: null },
          "display-3": { styles: null, demo: "Heading 2", font: null},
          "display-2": { styles: null, demo: "Heading 3", font: null},
          "display-1": { styles: null, demo: "Heading 4", font: null},
          "headline": { styles: null, demo: "Heading 5", font: null},
          "title": { styles: null, demo: "Heading 6", font: null},
          "subtitle-1": { styles: null, demo: "Subtitle 1", font: null},
          "subtitle-2": { styles: null, demo: "Subtitle 2", font: null},
          "body-1": { styles: null, demo: "Body 1", font: null},
          "body-2": { styles: null, demo: "Body 2", font: null},
          "caption": { styles: null, demo: "Caption", font: null},
          "overline": { styles: null, demo: "Overline", font: null},
          "v-btn": { styles: null, demo: "Button", font: null},
          "rai-data": { styles: null, demo: "Data $923.74% lI0O", font: null }
        },
        displayStyles: [
          "font-family",
          "font-size",
          "font-weight",
          "line-height",
          "letter-spacing",
          "text-decoration",
          "font-rendering",
          "font-variation-settings",
          "font-feature-settings",
        ],
      }
    },
    mounted() { 
      console.log('mounted')
      this.$nextTick(function() {
        var weights = {
          "100": "Thin",
          "200": "Extra Light",
          "300": "Light",
          "400": "Regular",
          "500": "Medium",
          "600": "Semi Bold",
          "700": "Bold",
          "800": "Extra Bold",
          "900": "Black",
        }
        for (const item in this.textStyles) {
          if (this.textStyles[item].styles === null) {
            var styles = this.cssObj(item)
            this.textStyles[item].styles = {}
            //this.textStyles[item].styles = this.cssObj(item)
            this.textStyles[item].font = styles['fontFamily'].split(",")[0].replace(/"/g, "")
            this.textStyles[item].weight = weights[styles['fontWeight']]
            this.textStyles[item].size = styles['fontSize']
          }
        }
      })
    },
   
    methods: {
        getStyle( element, property)
        {
            return window.getComputedStyle( element, null ).getPropertyValue( property );
        },
        getFont( ref )
        {
          return "font: " + cssObj(ref)['font-face']
        },
        cssObj( ref ) {
          return window.getComputedStyle(this.$refs[ref][0])
        }
    }
}
</script>