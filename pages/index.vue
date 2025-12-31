<template>
  <div class="product-page">
    <div class="product-container">
      <!-- LEFT -->
      <div class="product-carousel">
        <ImageCarousel :images="images" />
      </div>

      <!-- RIGHT -->
      <div class="product-table">
        <div class="spec-table">
          <p class="title">Mercedes-Benz</p>
          <p class="content">E200 AMG Line</p>

          <table>
            <tbody>
              <tr v-for="(value, key) in specs" :key="key">
                <td class="label">{{ key }}</td>
                <td class="value">{{ value }}</td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import ImageCarousel from '~/components/ImageCarousel.vue'

export default {
  components: {
    ImageCarousel
  },

  data() {
    const baseUrl =
      'https://media.oneweb.mercedes-benz.com/images/dynamic/asia/TH/236347/804/iris.png?q=COSY-EU-100-1713d0VXq0WLqtyO67PobzIr3eWsrrCsdRRzwQZg9pZbMw3SGtlaWtsd2HVcUfpOkXGEubSJ0l3IrOB2NS1bApj7oI5ux5xQC31CWkzNwPnm7jZeDhKV5Kh%25vqCuqyLRgc6YaxPa9rH1eMrn8wsbfoiZB5lM4FAmjTg95Yn6PDakDSeWHeutsd8ZDcUfiMcXGE4JmJ0lgOrOB2Pz%25bApe7pI5usKDQC3vSTkzNL6Sm%25kbFDZ1FtsdB%25ycJtj9GXOcSXqJ0l4YfOB2iMwbAp0ioI5u9GwQC3zgFkzN7PKm7jKGjhKUWP3IrZxD%25WLchARvVS%25qjuauQFQ0ZzKG1BZeEsRrbP76&BKGND=9&IMGT=P27&cp=U7lLKRUtPa6KAFr8s_ubHw&uni=m&POV='

    const imageUrls: string[] = []

    for (let i = 0; i <= 300; i += 10) {
      const beValue = `BE${String(i).padStart(3, '0')},PZM`
      imageUrls.push(`${baseUrl}${beValue}`)
    }
    return {
      images: imageUrls,
      specs: {
        'Type': 'GY',
        'Version': '35 TFSI',
        'Master Number': '137749178',
        'Type Approval Number': '1AC270',
        'Production From / To': '2020 -',
        'Engine Power (Kw/Ps)': '110 / 150',
        'System Power (Kw/Ps)': '180 / 210',
        'PCD': '5 / 112',
        'Center Bore': '57.1 mm',
        'Fuel': 'Hybrid Gasoline/E',
        'Axis Load Front': '1145 Kg',
        'Axis Load Rear': '1250 Kg',
        'Max Speed': '232'
      }
    }
  }
}
</script>