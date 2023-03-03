<template>
  <button
    type="button"
    class="btn btn-primary"
    data-bs-toggle="modal"
    data-bs-target="#myModal"
  >
    Register
  </button>
  <div id="myModal" class="modal fade" tabindex="-1">
    <div class="modal-dialog">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title">Register form</h5>
          <button
            type="button"
            class="btn-close"
            data-bs-dismiss="modal"
            aria-label="Close"
          ></button>
        </div>
        <div class="px-4 py-2">
          <div
            v-if="message"
            :class="alertClass"
            class="alert alert-primary"
            role="alert"
          >
            {{ message }}
          </div>
          <form
            id="form"
            @submit.prevent="submit()"
            class="needs-validation"
            novalidate
          >
            <div class="row mb-2">
              <div id="name" class="col-sm-6">
                <label for="validationCustom01" class="form-label"
                  >First name</label
                >
                <input
                  type="text"
                  class="form-control"
                  required
                  minlength="3"
                  maxlength="10"
                  pattern="[A-Za-z]+"
                  id="validationCustom01"
                />
                <div class="invalid-feedback">Please write your name.</div>

                <div class="valid-feedback">Looks good!</div>
              </div>
              <div id="surname" class="col-sm-6">
                <label for="validationCustom02" class="form-label"
                  >Last name</label
                >
                <input
                  type="text"
                  class="form-control"
                  required
                  minlength="3"
                  maxlength="10"
                  pattern="[A-Za-z]+"
                  id="validationCustom02"
                />
                <div class="invalid-feedback">Please write your surname.</div>
                <div class="valid-feedback">Looks good!</div>
              </div>
            </div>
            <div class="row mb-2">
              <div class="col-sm-5">
                <label for="validationCustomUsername" class="form-label"
                  >Username</label
                >
                <div class="input-group has-validation">
                  <span class="input-group-text" id="inputGroupPrepend">@</span>
                  <input
                    type="text"
                    class="form-control"
                    aria-describedby="inputGroupPrepend"
                    required
                    minlength="3"
                    maxlength="10"
                    id="validationCustomUsername"
                  />
                  <div class="invalid-feedback">Please choose a username.</div>
                </div>
              </div>
              <div class="col-sm-7">
                <label for="validationCustom03" class="form-label">Email</label>
                <input
                  id="validationCustom03"
                  type="email"
                  class="form-control"
                  required
                  minlength="3"
                />
                <div class="invalid-feedback">
                  Please provide a valid email.
                </div>
                <div class="valid-feedback">Looks good!</div>
              </div>
            </div>
            <div class="row mb-2">
              <div class="col-sm-5">
                <label for="validationCustom04" class="form-label">City</label>
                <input
                  type="text"
                  class="form-control"
                  required
                  minlength="3"
                  maxlength="10"
                  pattern="[A-Za-z]+"
                  id="validationCustom04"
                />
                <div class="invalid-feedback">Please provide a valid city.</div>
                <div class="valid-feedback">Looks good!</div>
              </div>
              <div class="col-sm-4">
                <label for="validationCustom05" class="form-label">State</label>
                <select id="validationCustom05" class="form-select" required>
                  <option selected disabled value="">Choose...</option>
                  <option>...</option>
                </select>
                <div class="invalid-feedback">Please select a valid state.</div>
              </div>
              <div class="col-sm-3">
                <label for="validationCustom06" class="form-label">Zip</label>
                <input
                  type="text"
                  class="form-control"
                  required
                  minlength="3"
                  maxlength="10"
                  pattern="^[0-9]+$"
                  id="validationCustom06"
                />
                <div class="invalid-feedback">Please provide a valid zip.</div>
              </div>
            </div>
            <div class="row mb-2">
              <div class="col-sm-6">
                <label for="validationCustom07" class="form-label"
                  >Password</label
                >
                <input
                  type="password"
                  class="form-control"
                  required
                  minlength="5"
                  maxlength="20"
                  pattern="^(?=.*[A-Z])(?=.*[^\w\s]).+$"
                  v-model="password"
                  id="validationCustom07"
                />
                <div class="invalid-feedback">
                  Password must include at least 1 capital letter and 1 symbol
                </div>
                {{ password }}
              </div>
              <div class="col-sm-6 row">
                <label for="male">Your Gender</label>
                <div class="form-check">
                  <input
                    id="male"
                    type="radio"
                    name="gender"
                    class="form-check-input"
                    required
                  />
                  <label for="male" class="form-check-label"> Male</label>
                </div>
                <div class="form-check">
                  <input
                    id="female"
                    type="radio"
                    name="gender"
                    class="form-check-input"
                  />
                  <label for="female" class="form-check-label"> Female</label>
                </div>
              </div>
            </div>

            <div>
              <div class="mb-3">
                <label for="inputGroupFile01" class="form-label">Image</label>
                <div class="input-group col-7">
                  <input
                    type="file"
                    class="form-control"
                    id="inputGroupFile01"
                    required
                  />
                  <label class="input-group-text" for="inputGroupFile01"
                    >Upload</label
                  >
                </div>
              </div>

              <div class="mb-2">
                <div class="form-check">
                  <input
                    id="invalidCheck"
                    class="form-check-input"
                    type="checkbox"
                    value=""
                    required
                  />
                  <label class="form-check-label" for="invalidCheck">
                    Agree to terms and conditions
                  </label>
                  <div class="invalid-feedback">
                    You must agree before submitting.
                  </div>
                </div>
              </div>
            </div>
          </form>
        </div>
        <div class="modal-footer">
          <button
            type="button"
            class="btn btn-secondary"
            data-bs-dismiss="modal"
          >
            Close
          </button>
          <button class="btn btn-primary" @click="submit" type="submit">
            Submit form
          </button>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      message: null,
      alertClass: "alert-danger",
      password: "",
    };
  },
  methods: {
    nameValidator(text) {
      let non_letter_regex = /[^a-zA-Z ]/;
      console.log(
        (text !== null || text.trim !== "") && !non_letter_regex.test(text)
          ? true
          : false
      );

      return (text !== null || text.trim !== "") && !non_letter_regex.test(text)
        ? true
        : false;
    },
    submit() {
      const form = document.getElementById("form");
      form.classList.add("was-validated");

      if (form.checkValidity()) {
        this.message = "Form sent succesfully!";
        this.alertClass = "alert-success";
      } else {
        this.message = "Check the inputs!";
        this.alertClass = "alert-danger";
      }
    },
  },
};
</script>
<style>
.container {
  width: auto;
}
</style>
