<template>
  <div class="container">
    <h1 style="margin-left: 20px; padding-top: 20px">Resume</h1>
    <div class="name-description">
      <h2>{{ name }}</h2>
      <p style="text-align: justify">{{ deskription }}</p>
    </div>
    <div class="experiences">
      <h2>Experiences</h2>
      <ol>
        <li
          class="li-pointer"
          v-for="(data, index) in experiences"
          @click="showDetail(data.show, index)"
          :key="data.id"
        >
          <p style="font-weight: 600">
            {{ data.start }} - {{ data.end }} - {{ data.experience }}
          </p>
          <p style="text-align: justify" v-if="data.show">
            {{ data.detail }}
          </p>
        </li>
      </ol>
    </div>
    <div class="skill">
      <h2>Skills</h2>
      <div v-for="data in skills" :key="skills">
        <ul>
          <li>
            <p>{{ data.skill }} ({{ data.value }}%)</p>
            <div
              :style="{
                width: data.value + '%',
                backgroundColor: '#04aa6d',
                height: 10 + 'px',
                maxWidth: 100 + '%',
              }"
            ></div>
          </li>
        </ul>
      </div>
    </div>
    <div class="contact-form">
      <h2>Contact Me</h2>
      <form @submit.prevent="onSubmit" ref="form">
        <p>Nama</p>
        <input v-model="contact.namecontact" required />
        <p>Email</p>
        <input type="email" v-model="contact.email" required />
        <p>Note</p>
        <textarea v-model="contact.note" cols="30" rows="10" required />
        <br />
        <button>Submit</button>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: "Naufal Dwi Ariananto",
      deskription:
        "Est labore incididunt voluptate aliqua ex incididunt nulla adipisicing mollit excepteur fugiat esse. Excepteur et nulla quis eu exercitation pariatur dolor ad est commodo dolor culpa laboris pariatur. Adipisicing reprehenderit nostrud est irure aute tempor Lorem anim in ullamco.",
      experiences: [
        {
          show: false,
          experience: "Junior FE Enginer at PT.Qatros",
          start: "Aug 2022",
          end: "Present",
          detail:
            "Ipsum Lorem elit reprehenderit incididunt Lorem non culpa magna commodo culpa ex quis. Dolore eu voluptate cupidatat proident nisi velit quis nulla adipisicing sint sunt quis et. Aliqua Lorem ipsum commodo ipsum excepteur proident id est eiusmod amet in. Duis quis quis occaecat fugiat veniam minim duis nisi enim quis reprehenderit.",
        },
        {
          show: false,
          experience: "Junior FE Enginer at PT.Qatros",
          start: "Aug 2022",
          end: "Present",
          detail:
            "Nostrud sint laborum deserunt proident laboris culpa dolore. Dolore est culpa labore qui elit ullamco ipsum do cillum. Laboris pariatur aute do eu Lorem excepteur eu commodo cupidatat esse dolor est. Minim magna eiusmod minim dolor et aute sit occaecat. Id sit eu ad sit deserunt. Aute sunt ea Lorem dolor amet occaecat anim aliqua ullamco tempor est non magna. Eiusmod tempor proident anim sit mollit.",
        },
        {
          show: false,
          experience: "Junior FE Enginer at PT.Qatros",
          start: "Aug 2022",
          end: "Present",
          detail:
            "Pariatur aute id dolore tempor et consequat elit tempor nulla. Eu velit proident exercitation fugiat elit ut fugiat nisi cillum magna deserunt deserunt. Ut veniam id enim labore qui aute. Adipisicing incididunt sint ut ullamco dolore incididunt enim exercitation cillum do voluptate. Adipisicing magna consectetur adipisicing eiusmod dolor nulla irure nisi. Aliqua officia laborum ipsum do mollit magna.",
        },
      ],
      skills: [
        { skill: "HTML", value: 40 },
        { skill: "JavaScript", value: 30 },
        { skill: "CSS", value: 30 },
      ],
      contact: { namecontact: "", email: "", note: "" },
    };
  },

  methods: {
    showDetail(experience, index) {
      this.experiences[index].show = !experience;
    },
    onSubmit() {
      if (
        !this.contact.namecontact ||
        !this.contact.email ||
        !this.contact.note
      ) {
        alert("Please finish the form");
        return;
      }
      alert(
        "Thank you " +
          this.contact.namecontact +
          ", we'll send you an email to " +
          this.contact.email +
          " regarding " +
          this.contact.note
      );
      this.$refs.form.reset()

    },
  },
};
</script>

<style>
.container {
  font-family: Cambria, Cochin, Georgia, Times, "Times New Roman", serif;
  width: 50%;
  margin: auto;
  background-color: #f2f2f2;
  border-radius: 12px;
}

h2 {
  font-weight: 500;
}

.li-pointer:hover {
  cursor: pointer;
}

.name-description {
  padding-left: 20px;
  padding-right: 20px;
}

.experiences {
  padding-left: 20px;
  padding-right: 20px;
}

.skill {
  padding-left: 20px;
  padding-right: 20px;
}

.contact-form {
  border-radius: 5px;
  background-color: #f2f2f2;
  padding: 20px;
}

input,
textarea {
  width: 100%;
  padding: 12px;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
  resize: vertical;
}

button {
  margin-top: 8px;
  background-color: #04aa6d;
  color: white;
  padding: 12px 20px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}
button:hover {
  background-color: #45a049;
}
</style>
