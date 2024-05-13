<template>
   <div class="cover-page base">
      <div class="cover-page-header">
         <div class="section-left">
            <img src="https://cdn.dev.reisetech.io/logo/gtsfly-logo.svg" alt="" width="180" />

            <div class="brands-wrapper">
               <div class="row">
                  <span class="brand-title">GTS Global Travel Services GmbH</span>
                  <span class="brand-address">Stresemannstr. 342 <br />D-22761 Hamburg</span>
               </div>
               <div class="row">
                  <span contenteditable class="brand-title">{{ model.brandName }}</span>
                  <span contenteditable class="brand-address" v-html="model.brandAddress"></span>
               </div>
            </div>
         </div>

         <div class="section-right">
            <img src="https://cdn.dev.reisetech.io/docgen/stamps/3.png" alt="" width="200" class="stamp" />
         </div>
      </div>
      <div class="cover-page-body">
         <!-- {{ model.title }} -->
         <div class="cover-page-title uppercase" contenteditable>
            {{ model.title }}
         </div>
         <!-- table header -->
         <div class="cover-page-info-table">
            <div class="table-col">
               <span class="table-title" contenteditable>{{ model.infoTable.invoiceNumber }}</span>
               <span class="table-info uppercase" contenteditable>{{ model.infoTable.invoiceNumberText }}</span>
            </div>
            <div class="table-col">
               <span class="table-title" contenteditable>{{ model.infoTable.customerNumber }}</span>
               <span class="table-info uppercase" contenteditable>{{ model.infoTable.customerNumberText }}</span>
            </div>
            <div class="table-col">
               <span class="table-title" contenteditable>{{ model.infoTable.servicePeriod }}</span>
               <span class="table-info uppercase" contenteditable>{{ model.infoTable.servicePeriodText }}</span>
            </div>
            <div class="table-col">
               <span class="table-title" contenteditable>{{ model.infoTable.date }}</span>
               <span class="table-info uppercase" contenteditable>{{ model.infoTable.dateText }}</span>
            </div>
         </div>
         <br />
         <br />
         <!-- price table header -->
         <div class="cover-page-price-table header">
            <div class="col">
               <span contenteditable>{{ model.priceTable.header.position }}</span>
            </div>
            <div class="col">
               <span contenteditable>{{ model.priceTable.header.description }}</span>
            </div>
            <div class="col">
               <span contenteditable>{{ model.priceTable.header.quantity }}</span>
            </div>
            <div class="col txt-right">
               <span contenteditable>{{ model.priceTable.header.total }}</span>
            </div>
         </div>

         <div class="cover-page-price-table body" v-for="(row, index) in model.priceTable.body" :key="index">
            <div class="col">
               <span contenteditable>{{ row.position }}</span>
            </div>
            <div class="col">
               <span contenteditable>{{ row.description }}</span>
            </div>
            <div class="col">
               <span contenteditable>{{ row.quantity }}</span>
            </div>
            <div class="col txt-right txt-bold">
               <span contenteditable>{{ row.total }}</span>
            </div>
         </div>
         <!-- Warning -->
         <p class="warning" contenteditable>{{ model.warning }}</p>
         <div class="button-wrapper do-not-print">
            <button class="add" @click="handlerAddRow">Add Row</button>
            <button class="delete" @click="handlerDeleteRow">Delete Row</button>
         </div>

         <div class="price-viewer-wrapper">
            <div class="price-viewer-inner-wrapper">
               <div class="row">
                  <div class="col">
                     <span contenteditable>{{ model.prices.subTotal }}</span>
                  </div>
                  <div class="col txt-right txt-bold">
                     <span contenteditable>{{ model.prices.subTotalText }}€</span>
                  </div>
               </div>
               <div class="row">
                  <div class="col">
                     <span contenteditable>{{ model.prices.tax }}</span>
                  </div>
                  <div class="col txt-right txt-bold">
                     <span contenteditable>{{ model.prices.taxText }}</span>
                  </div>
               </div>
               <div class="row">
                  <div class="col">
                     <span contenteditable>{{ model.prices.vat }}</span>
                  </div>
                  <div class="col txt-right txt-bold">
                     <span contenteditable>{{ model.prices.vatText }}€</span>
                  </div>
               </div>
               <div class="row">
                  <div class="col">
                     <span contenteditable> {{ model.prices.other }}</span>
                  </div>
                  <div class="col txt-right txt-bold">
                     <span contenteditable>{{ model.prices.otherText }}€</span>
                  </div>
               </div>
               <div class="row">
                  <div class="col">
                     <span contenteditable>{{ model.prices.total }}</span>
                  </div>
                  <div class="col txt-right txt-bold">
                     <span contenteditable>{{ model.prices.totalText }}€</span>
                  </div>
               </div>
            </div>
         </div>
      </div>

      <div class="cover-page-footer">
         <!-- Footer info badge -->
         <div class="footer-info-badge">
            <p contenteditable class="txt-bold txt-uppercase">{{ model.coverFooter.title }}</p>
            <p contenteditable class="txt-smaller" v-html="model.coverFooter.text"></p>
            <p></p>
         </div>

         <div id="fixedFooter" class="page-footer">
            <table class="footer-table">
               <tbody>
                  <tr class="txt-black trInvoiceFooterHeader">
                     <td class="footer-cell">GTS Global Travel Services GmbH</td>
                     <td class="footer-cell">Bankverbindung:</td>
                     <td class="footer-cell">Sitz der Gesellschaft: Hamburg</td>
                  </tr>
                  <tr class="trInvoiceFooter">
                     <td class="footer-cell">Stresemannstr. 342, 22761 Hamburg</td>
                     <td class="footer-cell">Commerzbank</td>
                     <td class="footer-cell">Amtsgericht: Hamburg</td>
                  </tr>
                  <tr class="trInvoiceFooter">
                     <td class="footer-cell">Tel.: +49 40-22 6 138 37-2</td>
                     <td class="footer-cell">IBAN: DE12 2004 0000 0632 1020 02</td>
                     <td class="footer-cell">HRB 118934</td>
                  </tr>
                  <tr class="trInvoiceFooter">
                     <td class="footer-cell">Fax.: +49 40-22 6 138 37-4</td>
                     <td class="footer-cell">BIC: COBADEFFXXX Swift: COBADEFF200</td>
                     <td class="footer-cell">Ust-IdNr.: DE 278135005</td>
                  </tr>
                  <tr class="trInvoiceFooter">
                     <td class="footer-cell">Email: buchhaltung@gtsfly.de</td>
                     <td class="footer-cell"></td>
                     <td class="footer-cell">GF: Serkan Yildiz/Ridvan Murteza</td>
                  </tr>
               </tbody>
            </table>
         </div>
      </div>
   </div>
</template>

<script>
export default {
   name: "PdfCover",
   props: {
      model: Object,
   },
   methods: {
      handlerAddRow() {
         this.$emit("add-row", {
            position: "2",
            description: "Hotelvermittlung",
            quantity: "19",
            total: "6.568,19",
         });
      },
      handlerDeleteRow() {
         this.$emit("delete-row");
      },
   },
};
</script>

<style lang="scss">
@media print {
   .do-not-print {
      display: none;
   }
}
.uppercase {
   text-transform: uppercase;
}
.txt-right {
   text-align: right;
}
.txt-smaller {
   font-size: 0.8rem;
}
.txt-bold {
   font-weight: 700;
}
.cover-page-title {
   font-size: 1.5rem;
   font-weight: 900;
   margin-bottom: 0.75rem;
}
.cover-page-info-table {
   width: 100%;
   min-height: 20px;
   border-radius: 0.5rem;
   border: 1.5px solid #363636;
   display: grid;
   grid-template-columns: 1.35fr 0.95fr 1.75fr 0.75fr;

   .table-col {
      padding: 1rem;
      border-right: 1.5px solid #363636;
      display: flex;
      flex-direction: column;

      span {
         &.table-title {
            font-size: 1rem;
            margin-bottom: 0.25rem;
         }
         &.table-info {
            font-size: 1.125rem;
            font-weight: 700;
         }
      }

      &:last-child {
         border-right: none;
      }
   }
}
.cover-page-price-table {
   width: 100%;
   min-height: 20px;
   display: grid;
   grid-template-columns: 1.25fr 2fr 1fr 1fr;
   .col {
      padding: 0.5rem 1rem;
      text-transform: capitalize;
   }

   &.header {
      background: #363636;
      color: #fff;

      .col {
         font-weight: 500;
      }
   }
   &.body {
      background: #f8faff;
      margin: 0.5rem 0;
      .col {
         padding: 0.5rem 1rem;
         text-transform: capitalize;
      }
   }
}
.warning {
   background: #f8faff;
   padding: 0.75rem 1rem;
   text-align: center;
   color: #d83838;
   font-weight: 500;
   text-transform: capitalize;
}
.button-wrapper {
   button {
      cursor: pointer;
      border: none;
      padding: 0.5rem 1rem;
      border-radius: 1rem;
      color: #fff;
      font-weight: 700;
      &:hover {
         transform: scale(1.05);
      }
      &.add {
         background-color: #61ee61;
         color: #363636;
      }
      &.delete {
         background-color: #ee6161;
      }
   }
}
.price-viewer-wrapper {
   margin-top: 2rem;
   width: 100%;
   display: flex;
   justify-content: flex-end;
   .price-viewer-inner-wrapper {
      width: fit-content;
      border: 2px solid #ccc;
      border-radius: 0.125rem;
      padding: 1rem;
      width: 300px;

      .row {
         display: flex;
         justify-content: space-between;
         margin-bottom: 0.75rem;

         &:last-child {
            margin-bottom: 0;
         }
      }
   }
}
.cover-page-footer {
   width: 100%;
   position: absolute;
   bottom: 0;

   left: 10mm;
   transform: translateX(-10mm);
   .footer-info-badge {
      p {
         margin: 0;
         margin-bottom: 0.25rem;
      }
   }
   .footer-informations {
      width: inherit;
      margin-top: 1rem;
      border-top: 2px solid #363636;
      display: grid;
      grid-template-columns: repeat(3, 1fr);
   }
}
.page-footer {
   margin-top: 1rem;
   padding-top: 1rem;
   border-top: 2px solid black;

   .footer-table {
      margin: 0;
      padding: 0;
      background: none;
      border: none;
      border-collapse: collapse;
      border-spacing: 0;
      background-image: none;
      width: 100%;

      .footer-cell {
         vertical-align: top;
         line-height: 1rem;
      }
   }

   .txt-black {
      font-weight: 700;
      font-size: 12px;
   }

   .trInvoiceFooter {
      font-size: 11px;
   }
}
.cover-page-header {
   padding-bottom: 0.5rem;
   margin-bottom: 1.5rem;
   border-bottom: 2px solid #363636;
   display: flex;
   justify-content: space-between;

   .stamp {
      opacity: 0.25;
   }

   img {
      margin-bottom: 1rem;
   }
   .brands-wrapper {
      width: fit-content;
      .row {
         display: flex;
         flex-direction: column;
         font-size: 0.7.5rem;
         border-bottom: 1px dashed #363636;
         padding-bottom: 0.75rem;
         margin-bottom: 0.75rem;

         &:last-child {
            border-bottom: none;
            padding-bottom: 0;
         }
         .brand-title {
            font-weight: 700;
         }
         .brand-address {
            // font-weight: 400;
         }
      }
   }
}
</style>
