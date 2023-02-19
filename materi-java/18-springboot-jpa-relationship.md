---
theme: gaia
_class: lead
paginate: true
backgroundColor: #fff
backgroundImage: url('https://marp.app/assets/hero-background.svg')
marp: true
---

![bg left:40% 60%](./../images/rawlabs-academy-logo.png)

# **Spring Boot JPA Relationship**
Rawlabs Academy

---
#### Database **Design**
![bg center: 70%](../images/materi-java/jpa-relationship/database-design.png)

---
### Constant **Enum**
![left h:500](../images/materi-java/jpa-relationship/constant.png)

---
![bg right:60% 90%](../images/materi-java/jpa-relationship/book-model.png)
### **Book** DAO
In the previous material, we have created a `Book` model and then adjust it as in the example

---
![bg right:53% 90%](../images/materi-java/jpa-relationship/author-model.png)
<style scoped>
    ul {
        font-size: 0.8rem;
    }
</style>
### **Author** DAO
- `@JsonIgnore` used for ignore field from json response
- `@OneToMany` based on DB design that mean the **Author** can have **many books**.
- `cascade` When we perform some action on the target entity, the same action will be applied to the associated entity
- `fetchType` how to fetch the data, `LAZY` is fetch **when needed** and `EAGER` fetch **immediatelly**

---
![bg right:60% 90%](../images/materi-java/jpa-relationship/category-model.png)
<style scoped>
    ul {
        font-size: 0.8rem;
    }
</style>
### **Category** DAO
- `@OneToMany` based on DB design that mean the **Category** can have **many books**.
- `fetchType` how to fetch the data, `LAZY` is fetch **when needed** and `EAGER` fetch **immediatelly**
- `mappedBy` to be used for mapping attribute on the **`Book` DAO**

---
![bg right:45% 90%](../images/materi-java/jpa-relationship/book-model-updated.png)
<style scoped>
    ul {
        font-size: 0.8rem;
    }
</style>
### Update the **Book** DAO
- `@ManyToOne` based on DB design that mean `Book` DAO have foreign key `author` and `category` then be mapped on each associated entity
- Foreign key will be generated automatically from `author` into `author_id` and `category` into `category_id` on database.

---
<!-- _class: lead -->
# Data Transfer Object
# **(DTO)**

---
![bg center: 90%](../images/materi-java/jpa-relationship/author-dto.png)

---
![bg center: 90%](../images/materi-java/jpa-relationship/category-dto.png)

---
![bg center: 90%](../images/materi-java/jpa-relationship/book-dto.png)

---
![bg center: 90%](../images/materi-java/jpa-relationship/stock-dto.png)

---
<!-- _class: lead -->
# Repository
# **(JPA Repository)**

---
![bg center: 90%](../images/materi-java/jpa-relationship/repository.png)

---
<style scoped>
    ul {
        font-size: 0.8rem;
    }
</style>
#### `BookRepository` Explanation
