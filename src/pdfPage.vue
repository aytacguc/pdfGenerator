<template>
   <button class="print do-not-print" @click="handlerPrint">Print</button>
   <section class="sheet padding-10mm">
      <CoverPage :model="model" @add-row="handlerAddNewRow" @delete-row="handlerDeleteRow" />
   </section>
   <section class="sheet padding-10mm landing">
      <TablePage :model="model" />
   </section>
</template>

<script>
// import model from "@/response.model.js";
import CoverPage from "./components/CoverPage.vue";
import TablePage from "./components/TablePage.vue";
export default {
   name: "App",
   components: {
      CoverPage,
      TablePage,
   },
   data() {
      return {
         editMode: false,
         model2: {
            title: "Invoice",
            infoTable: {
               invoiceNumber: "Rechnungsnummer",
               invoiceNumberText: "HCA2023-3963",
               customerNumber: "Kundennumer",
               customerNumberText: "123456",
               servicePeriod: "Leistungszeitraum",
               servicePeriodText: "04.10.2023 - 15.10.2023",
               date: "Datum",
               dateText: "26.10.2023",
            },
            priceTable: {
               header: {
                  position: "Postion",
                  description: "Beschreibung",
                  quantity: "Menge",
                  total: "Gesamt",
               },
               body: [
                  {
                     position: "1",
                     description: "Hotelvermittlung",
                     quantity: "19",
                     total: "6.568,19",
                  },
               ],
            },
            prices: {
               subTotal: "Zwischensumme",
               subTotalText: "6.568,19",
               tax: "Steuersatz",
               taxText: "0%",
               vat: "Umsatzsteuer",
               vatText: "0,00",
               other: "Andere",
               otherText: "0,00",
               total: "Gesamt",
               totalText: "6.568,19",
            },
            warning: "Details zu ihren Buchungen finden Sie im Anhang!",
            coverFooter: {
               title: "VIELEN DANK FÜR IHREN AUFTRAG",
               text: "Bitte überweisen Sie den Gesamtbetrag innerhalb von 10 Tagen ab Rechnungsstellung.<br>Bei Rückfragen stehen wir selbstverständlich jederzeit gerne zur Verfügung",
            },
            brandName: "Aurum Tours",
            brandAddress: "Frau Müller <br>Musterstr. 22 <br>1111 Muster",
         },
         model: {
            title: "Invoice",
            infoTable: {
               invoiceNumber: "Invoice Number",
               invoiceNumberText: "HCA2023-3963",
               customerNumber: "Agent Number",
               customerNumberText: "123456",
               servicePeriod: "Service Period",
               servicePeriodText: "04.10.2023 - 15.10.2023",
               date: "Date",
               dateText: "26.10.2023",
            },
            priceTable: {
               header: {
                  position: "Position",
                  description: "Description",
                  quantity: "Quantitiy",
                  total: "Total",
               },
               body: [
                  {
                     position: "1",
                     description: "Hotelvermittlung",
                     quantity: "19",
                     total: "6.568,19",
                  },
               ],
            },
            prices: {
               subTotal: "Sub Total",
               subTotalText: "6.568,19",
               tax: "Tax",
               taxText: "0%",
               vat: "Vat",
               vatText: "0,00",
               other: "Other",
               otherText: "0,00",
               total: "Grand Total",
               totalText: "6.568,19",
            },
            warning: "Details zu ihren Buchungen finden Sie im Anhang!",
            coverFooter: {
               title: "THANK YOU VERY MUCH FOR YOUR ORDER",
               text: "Please transfer the total amount within 10 days from the date of invoice.<br>If you have any questions, we are always happy to assist.",
            },
            brandName: "Aurum Tours",
            brandAddress: "Frau Müller <br>Musterstr. 22 <br>1111 Muster",
         },
      };
   },
   methods: {
      handlerPrint() {
         window.print();
      },
      handlerAddNewRow(row) {
         this.model.priceTable.body.push(row);
      },
      handlerDeleteRow() {
         this.model.priceTable.body.pop();
      },
   },
};
</script>

<style lang="scss">
.landing {
   width: 296mm !important;
   height: 210mm !important;
}
span,
p {
   &:hover {
      background-color: #f6ff0091;
   }
}
@page :first {
   size: A4;
}

/* Second page (landscape) */
@page {
   size: A4 landscape;
}

.base {
   height: 100%;
   position: relative;
}

input {
   border: 0;
}

.print {
   background: #363636;
   border: none;
   color: #fff;
   font-weight: 600;
   padding: 1rem 2rem;
   position: fixed;
   z-index: 99;
   left: 0;
   right: 0;
   margin: auto;
   width: fit-content;
   border-radius: 1rem;

   & {
      &:hover {
         cursor: pointer;
         transform: scale(1.1);
      }
   }
}
</style>
