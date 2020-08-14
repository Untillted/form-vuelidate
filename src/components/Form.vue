<template>
  <div class="container">
    <!-- --------------------------- BIO INFO ---------------------------------- -->
    <h1 class="form__title">Форма Регистрации</h1>
    <div>
      <form @submit.prevent="onSubmit" class="form__content" action>
        <!-- <MainInfo /> -->
        <div class="form__main main">
          <!-- SURNAME -->
          <div class="title">
            <h2>Общая информация</h2>
          </div>
          <div :class="{ input_error: $v.surname.$error }" class="main__col">
            <p class="main__text">* Фамилия</p>
            <input
              v-model.trim="$v.surname.$model"
              :class="{ error: $v.surname.$error }"
              @change="$v.surname.$touch()"
              class="input main__surname"
              type="text"
              placeholder="Введите Фамилию"
            />
            <p v-if="!$v.surname.required" class="text_warning">Введите Фамилию</p>
          </div>
          <!-- NAME -->
          <div :class="{ input_error: $v.name.$error }" class="main__col">
            <p class="main__text">* Имя</p>
            <input
              v-model.trim="$v.name.$model"
              :class="{ error: $v.name.$error }"
              @change="$v.name.$touch()"
              type="text"
              class="input main__name"
              placeholder="Введите имя"
            />
            <p v-if="!$v.name.required" class="text_warning">Введите Имя</p>
          </div>
          <!-- MIDDLE-NAME -->
          <div class="main__col">
            <p class="main__text">Отчество</p>
            <input type="text" class="input main__middle-name" placeholder="Введите Отчество" />
          </div>
          <!-- BIRTHDAY -->
          <div :class="{ input_error: $v.birthday.$error }" class="main__col">
            <p class="main__text">* Дата рождения</p>
            <input
              v-model.trim.lazy="$v.birthday.$model"
              :class="{ error: $v.birthday.$error }"
              @change="$v.birthday.$touch()"
              type="text"
              class="input main__birthday"
              placeholder="ДД.ММ.ГГ"
            />
            <p v-if="!$v.birthday.required" class="text_warning">Введите дату рождения</p>
            <p v-if="!$v.birthday.minLength" class="text_warning">Формат ввода ДД.ММ.ГГ</p>
          </div>
          <!-- PHONE -->
          <div :class="{ input_error: $v.phone.$error }" class="main__col">
            <p class="main__text">* Номер телефона</p>
            <input
              value="7"
              :class="{ error: $v.phone.$error }"
              v-model.number.lazy="$v.phone.$model"
              @change="$v.phone.$touch()"
              type="number"
              class="input main__phone"
              placeholder="Ваш номер начиная с 7"
            />
            <p v-if="!$v.phone.required" class="text_warning">Укажите номер телефона</p>
            <p v-if="!$v.phone.minLength" class="text_warning">11 значный номер</p>
            <p v-if="!$v.phone.maxLength" class="text_warning">Вы ввели больше 11 символов</p>
            <p v-if="!$v.phone.phoneValid" class="text_warning">Номер набран не с 7</p>
          </div>

          <!-- GENDER -->
          <div class="main__col">
            <p class="main__text">Ваш пол</p>
            <input type="text" class="input main__gender" placeholder="Укажите ваш пол" />
          </div>
          <!-- CLIENTS GROUP -->
          <div :class="{ input_error: $v.clients.$error }" class="main__col">
            <p class="main__text">* Ваша Группа</p>
            <select
              v-model="$v.clients.$model"
              @change="$v.clients.$touch()"
              :class="{ error: $v.clients.$error }"
              name="clients"
              size="3"
              multiple
              class="select form_group-clients"
            >
              <option value="VIP">VIP</option>
              <option value="Проблемные">Проблемные</option>
              <option value="ОМС">ОМС</option>
            </select>
            <p v-if="!$v.clients.required" class="text_warning">Выберите группу</p>
          </div>
          <!-- DOCTOR -->
          <div class="main__col">
            <p class="main__text">Лечащий врач</p>
            <select name="doctor" class="select main__doctor">
              <option selected disabled value>Выберите врача</option>
              <option value="Иванов">Иванов</option>
              <option value="Захаров">Захаров</option>
              <option value="Чернышева">Чернышева</option>
            </select>
          </div>
          <!-- SMS -->
          <div class="main__col main__col_sms">
            <label class="main__sms" for="sms">
              <input type="checkbox" id="sms" /> Не отправлять СМС
            </label>
          </div>
        </div>
        <!-- --------------------------- ADRESS DATA ---------------------------- -->
        <div class="form__adress adress">
          <div class="title">
            <h2>Данные вашего адресса</h2>
          </div>
          <!-- INDEX -->
          <div class="adress__col">
            <p class="adress__text">Индекс</p>
            <input class="input adress__index" type="number" placeholder="Введите Индекс" />
          </div>
          <!-- COUNTRY -->
          <div class="adress__col">
            <p class="adress__text">Страна</p>
            <input type="text" placeholder="Название вашей страны" class="input adress__country" />
          </div>
          <div class="adress__col">
            <p class="adress__text">Область</p>
            <input type="text" placeholder="Название вашей области" class="input adress__region" />
          </div>
          <!-- CITY -->
          <div :class="{ input_error: $v.city.$error }" class="adress__col">
            <p class="adress__text">* Город</p>
            <input
              v-model.trim="$v.city.$model"
              :class="{ error: $v.city.$error }"
              @change="$v.city.$touch()"
              type="text"
              placeholder="Имя вашего города"
              class="input adress__city"
            />
            <p v-if="!$v.city.required" class="text_warning">Неверно указан город</p>
            <p v-if="!$v.city.minLength" class="text_warning">Слишком короткое название</p>
          </div>
          <!-- STREET -->
          <div class="adress__col">
            <p class="adress__text">Улица</p>
            <input type="text" placeholder="Название вашей улицы" class="adress__street input" />
          </div>
          <!-- NUMBER HOME -->
          <div class="adress__col">
            <p class="adress__text">Дом</p>
            <input type="text" placeholder="Номер/Название дома" class="adress__number-home input" />
          </div>
        </div>
        <!-- ----------------------------- PASSPORT INFO --------------------------- -->
        <div class="form__passport passport">
          <div class="title">
            <h2>Данные вашего паспорта</h2>
          </div>
          <!-- DOCUMENTS -->
          <div :class="{ input_error: $v.documents.$error }" class="passport__col">
            <p class="passport__text">* Тип документа</p>
            <select
              v-model="$v.documents.$model"
              :class="{ error: $v.documents.$error }"
              @change="$v.documents.$touch()"
              name="documents"
              class="select passport__documents"
            >
              <option disabled value>Выберите тип документа</option>
              <option value="Паспорт">Паспорт</option>
              <option value="Свидетельство о рождении">Свидетельство о рождении</option>
              <option value="Вод. удостоверение">Вод. удостоверение</option>
            </select>
            <p v-if="!$v.documents.required" class="text_warning">Выберите Тип документа</p>
          </div>
          <!-- SERIES -->
          <div class="passport__col">
            <p class="passport__text">Серия</p>
            <input
              type="number"
              placeholder="Введите серию паспорта"
              class="input passport__series"
            />
          </div>
          <!-- NUMBER PASSPORT -->
          <div class="passport__col">
            <p class="passport__text">Номер</p>
            <input
              type="number"
              placeholder="Введите номер паспорта"
              class="input passport__number"
            />
          </div>
          <!-- ISSUED BY -->
          <div class="passport__col">
            <p class="passport__text">Кем выдан</p>
            <input type="text" placeholder="Кем выдан" class="input passport__issued" />
          </div>
          <!-- DATE  -->
          <div :class="{ input_error: $v.date.$error }" class="passport__col">
            <p class="passport__text">* Дата выдачи</p>
            <input
              type="text"
              v-model.trim="$v.date.$model"
              :class="{ error: $v.date.$error }"
              @change="$v.date.$touch()"
              class="input passport__date"
              placeholder="ДД.ММ.ГГ"
            />
            <p v-if="!$v.date.required" class="text_warning">Введите дату выдачи</p>
            <p v-if="!$v.date.minLength" class="text_warning">Формат ДД.ММ.ГГ</p>
          </div>
        </div>
        <div class="form__submitions">
          <button
            :disabled="submitStatus === 'PENDING'"
            type="submit"
            class="form__button"
          >Отправить</button>
          <p class="form__discription">Поля со * обязательны для заполнения!</p>
          <div v-if="submitStatus === 'ERROR'" class="overlay">
            <div class="modal">
              <p class="typo__p typo__p_error">Пожалуйста введите все данные!</p>
            </div>
          </div>
          <div v-if="submitStatus === 'OK'" class="overlay">
            <div class="modal">
              <p class="typo__p typo__p_ok">Форма отправлена!</p>
            </div>
          </div>
          <div v-if="submitStatus === 'PENDING'" class="overlay">
            <div class="modal">
              <p class="typo__p">Отправляю...</p>
            </div>
          </div>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
import {
  required,
  minLength,
  maxLength,
  withParams,
} from "vuelidate/lib/validators";

const isPhone = (value) => /^7/.test(value);

export default {
  components: {},
  data() {
    return {
      submitStatus: null,
      name: "",
      surname: "",
      birthday: "",
      phone: "",
      city: "",
      date: "",
      clients: [],
      documents: "",
    };
  },
  methods: {
    onSubmit() {
      this.$v.$touch();
      if (this.$v.$invalid) {
        this.submitStatus = "ERROR";
        setTimeout(() => {
          this.submitStatus = null;
        }, 2000);
      } else {
        this.submitStatus = "PENDING";
        setTimeout(() => {
          this.submitStatus = "OK";
          setTimeout(() => {
            this.submitStatus = null;
          }, 400);
        }, 1800);
      }
    },
  },
  validations: {
    name: {
      required,
    },
    documents: {
      required,
    },
    surname: {
      required,
    },
    birthday: {
      required,
      minLength: minLength(8),
    },
    phone: {
      required,
      phoneValid: isPhone,
      minLength: minLength(11),
      maxLength: maxLength(11),
    },
    city: {
      required,
      minLength: minLength(2),
    },
    date: {
      required,
      minLength: minLength(8),
    },
    clients: {
      required,
    },
  },
};
</script>

<style lang="scss">
// MAIN INFO
@import "@/style/main.scss";
// BIO INFO
@import "@/style/bio.scss";
// ADRESS INFO
@import "@/style/adress.scss";
// PASSPORT INFO
@import "@/style/passport.scss";
</style>
