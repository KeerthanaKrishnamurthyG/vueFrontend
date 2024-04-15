<template>
  <div>
    <div class="container">
      <div class="left">
        <div class="imgDiv">
          <img
            class="image-logo"
            :src="require('@/assets/kbzlogo.svg')"
            alt=""
          />
        </div>

        <div class="leftrouter">
          <!-- <div class="nav-items">
                <router-link class="nav-link" :to="{ name: 'Dashboard' }">
                  <div class="navLeft1">
                    <span class="nav-icon">👤</span>
                    <span class="nav-text">User Registered</span>
                  </div>
                </router-link>
                 <router-link class="nav-link" :to="{ name: 'Dashboard' }">
                  <div class="navLef2">
                      <span class="nav-icon">👨‍🚀</span>
                      <span class="nav-text">Help Centre</span>
                  </div>
                </router-link>
                 <router-link class="nav-link" :to="{ name: 'Dashboard' }">
                  <div class="navLef3">
                      <span class="nav-icon">⚙️</span>
                       <span class="nav-text">Admin</span>
                     
                  </div>
                </router-link>
        </div> -->
          <div class="left-navbar">
            <button class="nav-item" :class="{active: selectClickedBox==='userResigter'}" @click="selectClickedBox = 'userResigter' ">
              <img
                class="navIcon"
                :src="require('@/assets/userRegis.svg')"
                alt=""
              />
              <span class="nav-text">User Registered</span>
            </button>
              <button class="nav-item" :class="{active: selectClickedBox==='Help Centre'}" @click="selectClickedBox = 'Help Centre' ">
              <img
                class="navIcon"
                :src="require('@/assets/help-icon.svg')"
                alt=""
              />
              <span class="nav-text">Help Center</span>
            </button>
            <button class="nav-item" :class="{active: selectClickedBox==='Admins'}" @click="selectClickedBox = 'Admins' ">
              <img
                class="navIcon"
                :src="require('@/assets/admin.svg')"
                alt=""
              />
              <span class="nav-text">Admins</span>
            </button>
          </div>

          <div class="Logout">
            <div class="logLeft">
              <img :src="require('@/assets/imagelog.svg')" alt="" />
              <div class="imgText">
                <p class="logtext">Logged in as</p>
                <p class="logtextdown"> codeStax</p>
              </div>
            </div>
            <button class="logout-button">
              <img class="logoutImag" :src="require('@/assets/logoutIcon.svg')" alt="" />

            </button>
          </div>
        </div>
      </div>

      <div class="right">
        <div class="headPart">
          <span style="margin-right: 70%; white-space: nowrap"
            >User Registration</span
          >
         <div class="countryIcon">
          <img class="countryIconImg" :src="require('@/assets/country.svg')" alt="" />
         </div>
        </div>

        <div class="searchBox">
          <div>
            <v-text-field
              prepend-inner-icon="mdi-magnify"
              placeholder="Search"
              solo
              dense
            ></v-text-field>
          </div>
          <div>
            <button class="verify">
              <img :src="require('@/assets/scan-icon.svg')" alt="" />
              Verify User
            </button>
          </div>
        </div>

        <h>All Users(120)</h>
        <!-- <div class="innerTable"> -->

        <v-data-table
          fixed-header
          class="data-table"
          :headers="headers"
          pagination=false
          :sort-by="['Name', 'Company Name', 'Registered On ', 'Status']"
          :sort-desc="[false, false, false, false]"
          :items="userDetails"
          
        >
          <template v-slot:item.Status="{ item }">
            <button
              class="status-btn registered"
              v-if="item.Status == 'Registered'"
            >
              {{ item.Status }}
            </button>
            <button class="status-btn check-in" v-else>
              {{ item.Status }}
            </button>
          </template>
        </v-data-table>
        <!-- </div> -->
      </div>
    </div>
  </div>
</template>






<script>
export default {
  data() {
    return {
      selectClickedBox: 'userResigter',
      headers: [
        { text: "Name", value: "Name", class: "header" },
        { text: "Company", value: "Company" },
        { text: "Position", value: "Position" },
        { text: "Email", value: "Email" },
        { text: "PhoneNumber", value: "PhoneNumber" },
        { text: "RegisteredOn", value: "RegisteredOn" },
        { text: "Status", value: "Status", class: "statusColor" },
      ],
      userDetails: [
        {
          Name: "Khin",
          Company: "codestax.ai",
          Position: "sde",
          Email: "xyz@gmail.com",
          PhoneNumber: "123",
          RegisteredOn: "April 09,2024",
          Status: "Registered",
        },
        {
          Name: "Win",
          Company: "codestax.ai",
          Position: "sde2",
          Email: "yxz@gmail.com",
          PhoneNumber: "133",
          RegisteredOn: "Mar 09,2024",
          Status: "Checked in ",
        },
      ],
    };
  },
};
</script>




<style scoped>
* {
  margin: 0;
  padding: 0;
}

.status-btn.registered {
width: 96px;
height: 29px;
padding: 4px 0px 4px 0px;
gap: 0px;
border-radius: 4px 0px 0px 0px;
justify-content: space-between;
opacity: 0px;
background: #0055B126;
color: #0055B1;
}
.status-btn.check-in {
width: 96px;
height: 29px;
padding: 4px 0px 4px 0px;
gap: 0px;
border-radius: 4px 0px 0px 0px;
justify-content: space-between;
opacity: 0px;
background: #0055B126;
color:#0A7A30
}
.left-navbar {
  width: 100%;
  display: flex;
  flex-direction: column;
  gap: 16px;
  margin-top: 12px;
}

.Logout {
  width: 100%;
  height: 90px;
  padding: 21px 24px 21px 24px;
  gap: 0px;
  display:flex;
  justify-content: space-between;
  opacity: 0px;
  background: #0055b1;
}

.nav-item {
  width: 100%;
  display: flex;
  gap: 7px;
  padding: 8px 12px;
  align-items: center;
}
.logout-button{
  width: 48px;
height: 48px;
padding: 12px 0px 0px 0px;
gap: 8px;
border-radius: 4px 0px 0px 0px;
opacity: 0px;
background: #FFFFFF1F;



}



.imgText{
  display: flex;
  flex-direction: column;
  gap:4px;
}
/* 
.headPart{
  display: flex;
  width:100%;
  justify-content: space-between;
} */

.container {
  display: flex;
  width: 100%;
  padding: 10px;
  height: 100vh;
}
.navIcon {
  width: 24px;
  height: 24px;
  padding: 0.48px 0.56px 0.48px 0.48px;
  gap: 0px;
  opacity: 0px;
}
.left {
  width: 320px;
  height: 100%;
  /* padding: 40px 24px 0px 24px; */
  gap: 8px;
  opacity: 0px;
  display: flex;
  flex-direction: column;

  /* background-color: white;
  padding-bottom: 20%;
  width:20%;
  display: flex;
  padding:5px;
  flex-direction: column;

  padding-bottom: 40px; */
}
.headPart {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
    width:100%;
      margin-right: 60%;
  font-family: Inter;
  font-size: 24px;
  font-weight: 600;
  line-height: 36px;
  text-align: center;
}
.right {
  /* width: Fixed (1,600px)px;
height: Fixed (990px)px; */
  width: 100%;
  left: 320px;
  padding: 40px;
  gap: 24px;
  opacity: 0px;
  background-color: #f3f3f9;
  /* width: Fixed (1,600px)px;
height: Fixed (990px)px;
left: 320px;
padding: 40px 0px 0px 0px;
gap: 24px;
opacity: 0px;
 background: #F3F3F9;

  padding-right:40%;
  margin-left:20px; */
}
.leftrouter {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  flex-direction: column;
}
.nav-items {
  /* margin-left:20px; */
  background-color: white;
}

.header {
  background-color: blue !important;
}
.imgDiv {
  border-bottom: 1px solid #e0e0e0;
  padding-bottom: 12px;

  display: flex;
  justify-content: center;
}
.data-table {
  padding-top: 10px;
}

.data-table :deep(.v-data-footer){
  display: none !important;
}


.logLeft{
  display: flex;
  gap:8px;
  
}
.logtext{
  font-family: Inter;
font-size: 12px;
font-weight: 400;
line-height: 18px;
text-align: center;
color: #FFFFFF;
}
.logtextdown{
  font-family: Inter;
font-size: 16px;
font-weight: 600;
line-height: 24px;
text-align: center;
color: #FFFFFF;

}
/* .headPart {
  display: flex;
  margin-right: 60%;
  flex-direction: row;
} */

.leftNav {
  display: flex;
  align-items: center;
  flex-direction: column;
  padding: 0.5rem;
}

.selectBox {
  display: flex;
  margin-left: 135%;

  opacity: 0px;
}
.searchBox {
  display: flex;
  flex-grow: 1;
  justify-content: space-between;
}
.leftrouter {
  display: flex;
  flex-direction: columns;
  justify-content: space-between;
  height: 100%;
}
.navLeft1 {
  /* width: Fixed (272px)px;
height: Fixed (56px)px; */
  padding: 12px 16px 12px 16px;
  gap: 12px;
  border-radius: 8px 0px 0px 0px;
  opacity: 0px;
  background: #f3f3f9;
}
.navLeft2 {
  /* width: Fixed (272px)px;
height: Fixed (56px)px; */
  padding: 8px 12px 8px 12px;
  gap: 12px;
  border-radius: 4px 0px 0px 0px;
  opacity: 0px;
}
.navLeft3 {
  /* width: Fixed (272px)px;
height: Fixed (56px)px; */
  padding: 8px 12px 8px 12px;
  gap: 12px;
  border-radius: 4px 0px 0px 0px;
  opacity: 0px;
}
.button {
  padding: 10px;
  display: flex;
  justify-content: space-between;
}
.nav-items {
  margin-right: 10px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  /* width: Fill (272px)px;
height: Hug (200px)px; */
  gap: 16px;
  opacity: 0px;
}
.nav-link {
  width: Fixed (272px) px;
  height: Fixed (56px) px;
  padding: 12px 16px 12px 16px;
  gap: 12px;
  border-radius: 8px 0px 0px 0px;
  opacity: 0px;

  text-decoration: none;
  /* color: green; */
  /* color: var(--Neutral-Colors-Grey-400, var(--300, #788991)); */
  padding: 0.8em;
  display: flex;
  align-items: center;
  gap: 0.75em;
  border-radius: 0.5em;
}
.userDetails {
  display: flex;
  margin-top: 10px;
  flex-direction: row;
  justify-content: space-between;
}
.verify {
  /* display: flex;
  background-color: blue;
  color: black;
  padding: 3px;
  width: 87px;
height: 16px;
gap: 0px;
opacity: 0px; */

  width: 171px;
  height: 48px;
  padding: 16px 24px 16px 24px;
  gap: 12px;
  border-radius: 4px 0px 0px 0px;
  opacity: 0px;
  background: #0055b1;
  color: white;
  display: flex;
  gap: 10px;
}
.logoutImag{
  width: 24px;
height: 24px;
gap: 0px;
opacity: 0px;

}
.tablePart {
  border-collapse: collapse;
  border: 1px solid #ddd;
  margin-top: 10px;

  padding: 8px;
  width: 100px;
  padding-right: 20px;
}
.active{
  background: #F3F3F9;
  color: #0055B1;


}
.image-logo {
  width: 153px;
  height: 116px;
  gap: 0px;
  opacity: 0px;

  /* width: Hug (153px)px;
height: Hug (116px)px;
gap: 0px;
opacity: 0px;

  margin: 20px; */
}
</style>


// class overridden 

<style>
.theme--light.v-data-table.v-data-table--fixed-header thead th {
  background: blue !important;
  box-shadow: inset 0 -1px 0 rgba(0, 0, 0, 0.12);
}

.theme--light.v-data-table .v-data-table-header th.sortable:hover,
.theme--light.v-data-table .v-data-table-header th.sortable.active {
  color: white;
}

.theme--light.v-data-table > .v-data-table__wrapper > table > thead > tr > th {
    color: white;
}
</style>


