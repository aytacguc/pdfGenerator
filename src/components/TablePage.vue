<template>
   <div class="cover-page base" @click="handlerControl">
      <div class="excel-header">
         <div class="section-left">
            <img src="https://cdn.dev.reisetech.io/logo/gtsfly-logo.svg" alt="" width="150" />
         </div>
         <div class="section-right">
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
      </div>
      <div class="excel-table-wrapper">
         <div class="table-body">
            <div class="row header">
               <div class="col">
                  <span contenteditable> GTS OR. ID</span>
               </div>
               <div class="col">
                  <span contenteditable>Voucher</span>
               </div>
               <div class="col">
                  <span contenteditable>Transaction </span>
               </div>
               <div class="col">
                  <span contenteditable>Transs. Date </span>
               </div>
               <div class="col">
                  <span contenteditable>Check-in</span>
               </div>
               <div class="col">
                  <span contenteditable>Check-out</span>
               </div>
               <div class="col">
                  <span contenteditable>Room</span>
               </div>
               <div class="col">
                  <span contenteditable>Pax</span>
               </div>
               <div class="col">
                  <span contenteditable>Currency </span>
               </div>
               <div class="col">
                  <span contenteditable>Amount Payable</span>
               </div>
               <div class="col">
                  <span contenteditable>Hotel Name</span>
               </div>
               <div class="col">
                  <span contenteditable>City</span>
               </div>
               <div class="col">
                  <span contenteditable>Country</span>
               </div>
            </div>

            <div class="row" v-for="(row, index) in excel" :key="index">
               <div class="col">
                  <span contenteditable>
                     {{ row.gtsOrderId }}
                  </span>
               </div>
               <div class="col">
                  <span contenteditable> {{ row.voucher }} </span>
               </div>
               <div class="col">
                  <span class="booked" contenteditable> {{ row.transaction }} </span>
               </div>
               <div class="col">
                  <span contenteditable> {{ row.transactionDate }} </span>
               </div>
               <div class="col">
                  <span contenteditable> {{ row.checkIn }} </span>
               </div>
               <div class="col">
                  <span contenteditable> {{ row.checkOut }} </span>
               </div>
               <div class="col">
                  <span contenteditable> {{ row.Room }} </span>
               </div>
               <div class="col">
                  <span contenteditable> {{ row.Pax }} </span>
               </div>
               <div class="col">
                  <span contenteditable> {{ row.Currency }} </span>
               </div>
               <div class="col">
                  <span contenteditable> {{ row.amounPayable }} </span>
               </div>
               <div class="col">
                  <span contenteditable> {{ row.hotelName }} </span>
               </div>
               <div class="col">
                  <span contenteditable> {{ row.City }} </span>
               </div>
               <div class="col">
                  <span contenteditable> {{ row.Country }} </span>
               </div>
            </div>

            <!-- price -->

            <div class="row">
               <div class="col"><span>737136 </span></div>
               <div class="col"><span>MU9YN8L2 </span></div>
               <div class="col"><span>booked ✔ </span></div>
               <div class="col"><span>4/19/24 </span></div>
               <div class="col"><span>4/19/24 </span></div>
               <div class="col"><span>4/19/24 </span></div>
               <div class="col"><span>1 </span></div>
               <div class="col"><span>1 </span></div>
               <div class="col"><span>EUR </span></div>
               <div class="col showme" contenteditable>{{ excelTotal }} €</div>
               <div class="col"><span> </span></div>
               <div class="col"><span> </span></div>
               <div class="col"><span> </span></div>
            </div>
         </div>
         <div class="button-wrapper do-not-print">
            <button class="add" @click="handlerAddRow">Add Row</button>
            <button class="delete" @click="handlerDeleteRow">Delete Row</button>
         </div>
      </div>
   </div>
</template>

<script>
export default {
   name: "PdfCover",
   props: {
      model: Object,
      excel: Object,
      excelTotal: String,
   },
   methods: {
      handlerControl() {
         console.log("handlerControl");
      },
      handlerAddRow() {
         this.$emit("add-row", {
            gtsOrderId: "713377",
            voucher: "9DGCQEQD",
            transaction: "booked ✔",
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
         });
      },
      handlerDeleteRow() {
         this.$emit("delete-row");
      },
   },
};
</script>

<style lang="scss" scoped>
span {
   text-transform: capitalize;
}
.excel-table-wrapper {
   .table-body {
      .row {
         display: grid;
         grid-template-columns: 0.75fr 0.75fr 0.75fr 0.75fr 0.75fr 0.75fr 0.35fr 0.35fr 0.5fr 1fr 2fr 0.65fr 0.65fr;
         background: #ebeef5;
         margin-bottom: 0.5rem;
         border-radius: 24rem;
         // display: flex;
         // align-items: center;

         &.header {
            background-color: #363636 !important;

            .col {
               color: #fff;
               font-size: 0.75rem !important;
            }
         }

         .col {
            font-size: 0.75rem;
            flex: 1;
            padding: 0.75rem 0.5rem;
            // border: 1px solid #ccc;

            span.booked {
               background: #ccffdc;
               padding: 0.25rem 0.75rem;
               border-radius: 1rem;
               color: #209947;
               font-weight: 600;
            }
         }

         &:nth-child(odd) {
            background: #fff;
            border: 1px solid #ccc;
         }

         &:last-child {
            color: #fff;
            border: none;
            background: transparent;

            .col {
               &.showme {
                  color: #363636;
                  font-weight: 700;
               }
            }
         }
      }
   }
}
.excel-header {
   display: flex;
   justify-content: space-between;
   margin-bottom: 1.5rem;

   .section-right {
      display: flex;

      .table-col {
         display: flex;
         flex-direction: column;
         border-right: 1px solid #363636;
         justify-content: center;
         padding-right: 2rem;
         margin-right: 2rem;

         &:last-child {
            border-right: none;
            padding-right: 0;
            margin-right: 0;
         }

         .table-title {
            font-size: 0.85rem;
            margin-bottom: 0.125rem;
         }
         .table-info {
            font-weight: 600;
         }
      }
   }
}
</style>
