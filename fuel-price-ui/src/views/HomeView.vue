<script>
import { BASE_SERVICE_URL } from "../constants";
export default {
  data: () => ({
    text: "Form is valid.",
    form_submitted: false,
    form_data: {},
    valid: true,
    email: "",
    emailRules: [
      (v) => !!v || "E-mail is required",
      (v) => /.+@.+\..+/.test(v) || "E-mail must be valid",
    ],
    select: null,
    items: [
      { displayText: "Unleaded Petrol (U91)", value: "1" },
      { displayText: "Premium Unleaded (U95)", value: "2" },
      { displayText: "98 RON (U98)", value: "6" },
      { displayText: "E85", value: "10" },
      { displayText: "Diesel", value: "4" },
      { displayText: "Brand diesel", value: "11" },
      { displayText: "LPG", value: "5" },
    ],
    suburb: "",
    suburbs: [
      "Alexander Heights",
      "Alfred Cove",
      "Alkimos",
      "Anketell",
      "Applecross",
      "Ardross",
      "Armadale",
      "Ascot",
      "Ashby",
      "Ashendon",
      "Ashfield",
      "Attadale",
      "Atwell",
      "Aubin Grove",
      "Aveley",
      "Avon Valley National Park",
      "Bailup",
      "Balcatta",
      "Baldivis",
      "Balga",
      "Ballajura",
      "Banksia Grove",
      "Banksiadale",
      "Banjup",
      "Barragup",
      "Baskerville",
      "Bassendean",
      "Bateman",
      "Bayswater",
      "Beaconsfield",
      "Beckenham",
      "Bedford",
      "Bedfordale",
      "Beechboro",
      "Beechina",
      "Beeliar",
      "Beldon",
      "Belhus",
      "Bellevue",
      "Belmont",
      "Bennett Springs",
      "Bentley",
      "Bertram",
      "Bibra Lake",
      "Bickley",
      "Bicton",
      "Birchmont",
      "Blythewood",
      "Booragoon",
      "Bouvard",
      "Boya",
      "Brabham",
      "Brentwood",
      "Brigadoon",
      "Brookdale",
      "Bull Creek",
      "Bullsbrook",
      "Bushmead",
      "Burns Beach",
      "Burswood",
      "Butler",
      "Byford",
      "Calista",
      "Canning Mills",
      "Canning Vale",
      "Cannington",
      "Camillo",
      "Carabooda",
      "Cardup",
      "Carine",
      "Carlisle",
      "Carmel",
      "Carramar",
      "Casuarina",
      "Caversham",
      "Champion Lakes",
      "Chidlow",
      "Churchlands",
      "City Beach",
      "Claremont",
      "Clarkson",
      "Clifton",
      "Cloverdale",
      "Cockburn Central",
      "Como",
      "Connolly",
      "Coodanup",
      "Coogee",
      "Coolbellup",
      "Coolbinia",
      "Cooloongup",
      "Coolup",
      "Cottesloe",
      "Craigie",
      "Crawley",
      "Cullacabardee",
      "Currambine",
      "Daglish",
      "Dalkeith",
      "Darch",
      "Darling Downs",
      "Darlington",
      "Dawesville",
      "Dayton",
      "Dianella",
      "Doubleview",
      "Dudley Park",
      "Duncraig",
      "Dwellingup",
      "East Cannington",
      "East Fremantle",
      "East Perth",
      "East Rockingham",
      "East Victoria Park",
      "Eden Hill",
      "Edgewater",
      "Eglinton",
      "Ellenbrook",
      "Embleton",
      "Erskine",
      "Etmilyn",
      "Falcon",
      "Fairbridge",
      "Ferndale",
      "Floreat",
      "Forrestdale",
      "Forrestfield",
      "Fremantle",
      "Furnissdale",
      "Garden Island",
      "Gidgegannup",
      "Girrawheen",
      "Glen Forrest",
      "Glendalough",
      "Gnangara",
      "Golden Bay",
      "Gooseberry Hill",
      "Gorrie",
      "Gosnells",
      "Greenfields",
      "Greenmount",
      "Greenwood",
      "Guildford",
      "Gwelup",
      "Hacketts Gully",
      "Halls Head",
      "Hamersley",
      "Hamilton Hill",
      "Hammond Park",
      "Harrisdale",
      "Haynes",
      "Hazelmere",
      "Heathridge",
      "Helena Valley",
      "Henderson",
      "Henley Brook",
      "Herdsman",
      "Herne Hill",
      "Herron",
      "Highgate",
      "High Wycombe",
      "Hilbert",
      "Hillarys",
      "Hillman",
      "Hilton",
      "Hocking",
      "Holyoake",
      "Hopeland",
      "Hope Valley",
      "Hovea",
      "Huntingdale",
      "Iluka",
      "Inglehope",
      "Inglewood",
      "Innaloo",
      "Jandabup",
      "Jandakot",
      "Jane Brook",
      "Jarradale",
      "Jindalee",
      "Jolimont",
      "Joondalup",
      "Joondanna",
      "Kalamunda",
      "Kallaroo",
      "Karawara",
      "Kardinya",
      "Karnup",
      "Karragullen",
      "Karrakatta",
      "Karrakup",
      "Karrinyup",
      "Kelmscott",
      "Kensington",
      "Kenwick",
      "Keralup",
      "Kewdale",
      "Keysbrook",
      "Kiara",
      "Kings Park",
      "Kingsley",
      "Kinross",
      "Koondoola",
      "Koongamia",
      "Kwinana Beach",
      "Kwinana Town Centre",
      "Lake Coogee",
      "Lakelands",
      "Landsdale",
      "Langford",
      "Lathlain",
      "Leda",
      "Leederville",
      "Lesley",
      "Leeming",
      "Lesmurdie",
      "Lexia",
      "Lockridge",
      "Lynwood",
      "Maddington",
      "Madeley",
      "Madora Bay",
      "Mahogany Creek",
      "Maida Vale",
      "Malaga",
      "Malmalling",
      "Mandogalup",
      "Mandurah",
      "Manning",
      "Marangaroo",
      "Mardella",
      "Mariginiup",
      "Marmion",
      "Marrinup",
      "Martin",
      "Maylands",
      "Meadow Springs",
      "Medina",
      "Meelon",
      "Melaleuca",
      "Melville",
      "Menora",
      "Merriwa",
      "Middle Swan",
      "Midland",
      "Midvale",
      "Millendon",
      "Mindarie",
      "Mirrabooka",
      "Morley",
      "Mosman Park",
      "Mount Claremont",
      "Mount Hawthorn",
      "Mount Helena",
      "Mount Lawley",
      "Mount Nasura",
      "Mount Pleasant",
      "Mount Richon",
      "Mullaloo",
      "Mundaring",
      "Mundijong",
      "Munster",
      "Murdoch",
      "Myaree",
      "Myara",
      "Naval Base",
      "Nambeelup",
      "Nedlands",
      "Neerabup",
      "Nirimba",
      "Nollamara",
      "Noranda",
      "North Beach",
      "Northbridge",
      "North Coogee",
      "North Dandalup",
      "North Fremantle",
      "North Lake",
      "North Perth",
      "North Yunderup",
      "Nowergup",
      "Oakford",
      "Oakley",
      "Ocean Reef",
      "O'Connor",
      "Oldbury",
      "Orange Grove",
      "Orelia",
      "Osborne Park",
      "Padbury",
      "Palmyra",
      "Parkerville",
      "Parklands",
      "Parkwood",
      "Parmelia",
      "Paulls Valley",
      "Pearsall",
      "Peel Estate",
      "Peppermint Grove",
      "Peron",
      "Perth",
      "Perth Airport",
      "Piara Waters",
      "Pickering Brook",
      "Piesse Brook",
      "Pinjar",
      "Pinjarra",
      "Point Grey",
      "Port Kennedy",
      "Postans",
      "Queens Park",
      "Quinns Rocks",
      "Redcliffe",
      "Ravenswood",
      "Red Hill",
      "Ridgewood",
      "Riverton",
      "Rivervale",
      "Rockingham",
      "Roleystone",
      "Rossmoyne",
      "Safety Bay",
      "Saint James",
      "Salter Point",
      "Samson",
      "San Remo",
      "Sawyers Valley",
      "Scarborough",
      "Secret Harbour",
      "Serpentine",
      "Seville Grove",
      "Shelley",
      "Shenton Park",
      "Shoalwater",
      "Silver Sands",
      "Sinagra",
      "Singleton",
      "Solus",
      "Sorrento",
      "Southern River",
      "South Fremantle",
      "South Guildford",
      "South Lake",
      "South Perth",
      "South Yunderup",
      "Spearwood",
      "Stake Hill",
      "Stirling",
      "Stoneville",
      "Stratton",
      "Subiaco",
      "Success",
      "Swanbourne",
      "Swan View",
      "Tamala Park",
      "Tapping",
      "Teesdale",
      "The Lakes",
      "The Spectacles",
      "The Vines",
      "Thornlie",
      "Treeby",
      "Trigg",
      "Tuart Hill",
      "Two Rocks",
      "Upper Swan",
      "Victoria Park",
      "Viveash",
      "Waikiki",
      "Walliston",
      "Walyunga National Park",
      "Wandi",
      "Wangara",
      "Wannanup",
      "Wanneroo",
      "Warnbro",
      "Warwick",
      "Waterford",
      "Watermans Bay",
      "Wattle Grove",
      "Wattleup",
      "Wellard",
      "Welshpool",
      "Wembley",
      "Wembley Downs",
      "West Coolup",
      "West Leederville",
      "West Perth",
      "West Pinjarra",
      "West Swan",
      "Westminster",
      "Whitby",
      "White Gum Valley",
      "Whiteman",
      "Whittaker",
      "Willagee",
      "Willetton",
      "Wilson",
      "Winthrop",
      "Woodbridge",
      "Woodlands",
      "Woodvale",
      "Wooroloo",
      "Wungong",
      "Yanchep",
      "Yangebup",
      "Yokine",
      "Yunderup",
    ],
  }),

  methods: {
    reset() {
      this.$refs.form.reset();
    },
    submit() {
      this.form_submitted = true;
      this.form_data = {
        fuel_type: this.select.displayText,
        email: this.email,
        suburb: this.suburb,
      };
      fetch(BASE_SERVICE_URL + "addSubscription", {
        method: "POST",
        headers: {
          "Content-Type": "application/json",
        },
        body: JSON.stringify({
          product: this.select.value,
          email: this.email,
          suburb: this.suburb,
        }),
      })
        .then(() => {
          this.$refs.form.reset();
        })
        .catch(() => {});
    },
    unsubscribe() {
      this.$router.push("/unsubscribe");
    },
  },
};
</script>

<template>
  <h2><strong>Fuel price for metropolitan suburbs</strong></h2>
  <br />
  <v-form ref="form" v-model="valid" lazy-validation>
    <div class="text-center">
      <v-dialog v-model="form_submitted" style="max-width: 640px">
        <v-card>
          <v-card-text>
            Your have successfully subscribed to fuel price emails. The current
            subscription has the following details:
            <p>
              <strong>Fuel type - {{ form_data.fuel_type }}</strong>
            </p>
            <p>
              <strong>Suburb - {{ form_data.suburb }}</strong>
            </p>
            <p>
              <strong>Email - {{ form_data.email }}</strong>
            </p>
            <br />
            <p>
              <strong>
                <i
                  >If you think the subscription details are incorrect. Please
                  unsubscribe and create a new subscription with correct
                  details.</i
                >
              </strong>
            </p>
          </v-card-text>
          <v-card-actions>
            <v-btn color="primary" block @click="form_submitted = false"
              >Close</v-btn
            >
          </v-card-actions>
        </v-card>
      </v-dialog>
    </div>

    <v-select
      v-model="select"
      :items="items"
      item-title="displayText"
      item-value="value"
      return-object
      single-line
      :rules="[(v) => !!v || 'Fuel type is required']"
      label="Fuel type"
      required
    ></v-select>

    <br />

    <v-autocomplete
      v-model="suburb"
      clearable
      label="Suburb"
      hint="Type the first few letters of your suburb and select the appropriate one from the list"
      persistent-hint
      :items="suburbs"
      :rules="[(v) => !!v || 'Suburb is required']"
    ></v-autocomplete>
    <br />

    <v-text-field
      v-model="email"
      :rules="emailRules"
      label="E-mail"
      required
    ></v-text-field>

    <v-btn color="success" class="mr-4" @click="submit" :disabled="!valid">
      Subscribe
    </v-btn>

    <v-btn color="warning" class="mr-4" @click="reset"> Reset Form </v-btn>
  </v-form>
  <br />
  <br />
  <v-btn color="error" block @click="unsubscribe">
    Click here to unsubscribe
  </v-btn>
  <br />
  <br />
  <v-expansion-panels>
    <v-expansion-panel
      title="How it works?"
      text="Once you subscribe, you will receive an email everyday after 2.30PM containing prices for today and tomorrow for your nominated suburb (and surrounding suburbs) and fuel type. You can create multiple subscriptions for different fuel types and suburbs."
    >
      <div class="text-center">
        <a href="https://www.fuelwatch.wa.gov.au/" target="_blank"
          >Source of fuel prices</a
        >
      </div>
      <div class="text-center">
        <a
          href="https://www0.landgate.wa.gov.au/maps-and-imagery/wa-geographic-names/name-history/historical-suburb-names"
          target="_blank"
          >Source of suburbs</a
        >
      </div>
    </v-expansion-panel>
  </v-expansion-panels>
</template>
