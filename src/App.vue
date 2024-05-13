<template>
   <button class="print do-not-print" @click="handlerPrint">Print</button>

   <section class="sheet padding-10mm">
      <CoverPage :model="model" @add-row="handlerAddNewRow" @delete-row="handlerDeleteRow" />
   </section>
   <section class="sheet padding-10mm landing">
      <TablePage :model="model" :excel="excel" :excelTotal="excelTotal" @add-row="handlerAddNewRowExcel" @delete-row="handlerDeleteRowExcel" />
   </section>
</template>

<script>
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
         excel: [
            {
               gtsOrderId: "713377",
               voucher: "9DGCQEQD",
               transaction: "booked",
               transactionDate: "4/3/24",
               checkIn: "4/4/24",
               checkOut: "4/6/24",
               Room: "1",
               Pax: "1",
               Currency: "EUR",
               amounPayable: "318.15 €",
               hotelName: "Radisson Collection  Hotel, Vadistanbul",
               City: "Istanbul",
               Country: "Türkiye",
            },
            {
               gtsOrderId: "714262",
               voucher: "LXPMBJKR",
               transaction: "booked",
               transactionDate: "4/4/24",
               checkIn: "4/22/24",
               checkOut: "4/24/24",
               Room: "1",
               Pax: "2",
               Currency: "EUR",
               amounPayable: "140.59 €",
               hotelName: "Hotel The Pera Hill",
               City: "Istanbul",
               Country: "Türkiye",
            },
            {
               gtsOrderId: "720802",
               voucher: "BPBQUJHE",
               transaction: "booked",
               transactionDate: "4/9/24",
               checkIn: "4/10/24",
               checkOut: "4/13/24",
               Room: "1",
               Pax: "2",
               Currency: "EUR",
               amounPayable: "432.60 €",
               hotelName: "DoubleTree by Hilton  Hotel Istanbul - Sirkeci",
               City: "Istanbul",
               Country: "Türkiye",
            },
            {
               gtsOrderId: "716206",
               voucher: "9AXTLUDV",
               transaction: "booked",
               transactionDate: "4/5/24",
               checkIn: "4/25/24",
               checkOut: "4/27/24",
               Room: "1",
               Pax: "2",
               Currency: "EUR",
               amounPayable: "143.38 €",
               hotelName: "Hotel The Pera Hill",
               City: "Istanbul",
               Country: "Türkiye",
            },
            {
               gtsOrderId: "719757",
               voucher: "OSWRUPHX",
               transaction: "booked",
               transactionDate: "4/8/24",
               checkIn: "4/19/24",
               checkOut: "4/22/24",
               Room: "1",
               Pax: "2",
               Currency: "EUR",
               amounPayable: "305.91 €",
               hotelName: "Skalion Hotel & SPA",
               City: "Istanbul",
               Country: "Türkiye",
            },
            {
               gtsOrderId: "719716",
               voucher: "AQKRDWJA",
               transaction: "booked",
               transactionDate: "4/8/24",
               checkIn: "4/28/24",
               checkOut: "4/30/24",
               Room: "1",
               Pax: "3",
               Currency: "EUR",
               amounPayable: "175.10 €",
               hotelName: "Beyazit Palace Hotel",
               City: "Istanbul",
               Country: "Türkiye",
            },
            {
               gtsOrderId: "757606",
               voucher: "PWFGM3GH",
               transaction: "booked",
               transactionDate: "4/29/24",
               checkIn: "4/29/24",
               checkOut: "5/4/24",
               Room: "1",
               Pax: "2",
               Currency: "EUR",
               amounPayable: "618.00 €",
               hotelName: "Hotel Yasmak Sultan",
               City: "Istanbul",
               Country: "Türkiye",
            },
            {
               gtsOrderId: "754186",
               voucher: "YFX6HHV5",
               transaction: "booked",
               transactionDate: "4/27/24",
               checkIn: "4/29/24",
               checkOut: "5/4/24",
               Room: "2",
               Pax: "4",
               Currency: "EUR",
               amounPayable: "968.20 €",
               hotelName: "Ramada by Wyndham Is tanbul Taksim",
               City: "Istanbul",
               Country: "Türkiye",
            },
            {
               gtsOrderId: "729139",
               voucher: "UGYFP8HO",
               transaction: "booked",
               transactionDate: "4/14/24",
               checkIn: "4/18/24",
               checkOut: "4/21/24",
               Room: "1",
               Pax: "2",
               Currency: "EUR",
               amounPayable: "262.65 €",
               hotelName: "Ramada by Wyndham Is tanbul Taksim",
               City: "Istanbul",
               Country: "Türkiye",
            },
            {
               gtsOrderId: "745447",
               voucher: "AZPUIYCM",
               transaction: "booked",
               transactionDate: "4/23/24",
               checkIn: "4/24/24",
               checkOut: "4/26/24",
               Room: "1",
               Pax: "1",
               Currency: "EUR",
               amounPayable: "118.66 €",
               hotelName: "Hotel The Pera Hill",
               City: "Istanbul",
               Country: "Türkiye",
            },
            {
               gtsOrderId: "726221",
               voucher: "KVQETB3Y",
               transaction: "booked",
               transactionDate: "4/12/24",
               checkIn: "4/12/24",
               checkOut: "4/13/24",
               Room: "1",
               Pax: "2",
               Currency: "EUR",
               amounPayable: "67.09 €",
               hotelName: "Grand Makel Hotel To pkapi",
               City: "Istanbul",
               Country: "Türkiye",
            },
            {
               gtsOrderId: "737136",
               voucher: "MU9YN8L2",
               transaction: "booked",
               transactionDate: "4/18/24",
               checkIn: "4/19/24",
               checkOut: "4/20/24",
               Room: "1",
               Pax: "2",
               Currency: "EUR",
               amounPayable: "88.99 €",
               hotelName: "Doubletree by Hilton  İstanbul Umraniye",
               City: "Istanbul",
               Country: "Türkiye",
            },
            //fason
         ],
         excelTotal: "3.639,32",
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
      handlerAddNewRowExcel(row) {
         this.excel.push(row);
      },
      handlerDeleteRowExcel() {
         this.excel.pop();
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
