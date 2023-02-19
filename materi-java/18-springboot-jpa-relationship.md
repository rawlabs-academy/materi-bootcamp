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
    p, ul {
        font-size: 0.9rem;
    }
    p > strong {
        color: purple;
    }
</style>
#### `BookRepository` Explanation

The query **"select b from Book b where upper(b.category.name) like upper(:category) and upper(b.author.name) like upper(:author)"** is Java Persistence Query Language **(JPQL)**

It will be translated into SQL by **"select b.\* from book b join category c on c.id = b.category_id join author a on a.id = b.author_id where upper(c.name) like upper(:category) and upper(a.name) like upper(:author)"** on native query language.

---
<!-- _class: lead -->
<style>
    h1 {
        font-size: 3.5rem;
    }
</style>
# **Service**

---
![bg right:60% 90%](../images/materi-java/jpa-relationship/author-service.png)
### **Author** Service

The `AuthorService` will be used to create new author of the book.

---
![bg right:60% 90%](../images/materi-java/jpa-relationship/category-service.png)
### **Category** Service

The `CategoryService` will be used to create new category of the book.

---
![bg center: 80%](../images/materi-java/jpa-relationship/book-service-dependency.png)
### Book Service `Dependency` Injection

---
![bg right:65% 90%](../images/materi-java/jpa-relationship/book-service-save.png)
<style scoped>
    ul {
        font-size: 0.8rem;
    }
</style>
### Save Book `BookService`
- The flow is, find the `author` and `category` first because the `book` have relation to `author` and `category`
- Line **18 - 19** is set attribute **association**

---
![bg right:60% 90%](../images/materi-java/jpa-relationship/book-service-get-list.png)
<style scoped>
    p {
        font-size: 0.8rem;
    }
</style>
### Get List Book `Book Service`
**Why not direct use book repository?**

`Author` and `Category` have `OneToMany` relation. It can be used to get many book where have foreign key of each **Author** or **Category**

---
![bg right:60% 90%](../images/materi-java/jpa-relationship/book-service-update-stock.png)
<style scoped>
    p {
        font-size: 0.8rem;
    }
</style>
### Update Stock `BookService`

The flow is find book by id first if book is empty will return an exception.

If **StockType** is `ADDITIONS` that mean stock will be **added** by request value.

or if **StockType** is `REDUCTION` that mean stock will be **reducted** by request value

---
<!-- _class: lead -->
<style scoped>
    h1 {
        font-size: 3.5rem;
    }
</style>
# **Controller**

---
![bg right:70% 90%](../images/materi-java/jpa-relationship/author-controller.png)
### **Author** Controller

---
![bg right:70% 90%](../images/materi-java/jpa-relationship/category-controller.png)
### **Category** Controller

---
![bg right:60% 90%](../images/materi-java/jpa-relationship/book-controller-get-list-book.png)
<style scoped>
    ul {
        font-size: 0.75rem;
    }
</style>
### Get List Book
- If request param `author` and `category` is not empty will be get list book by author and category
- if request param only `author` is not empty will be get list book by author
- if request param only `category` is not empty will be get list book by category
- Or else get all books

---
### Update Book Stock
![right h:350](../images/materi-java/jpa-relationship/book-controller-update-stock.png)

---
<!-- _class: lead -->
<style scoped>
    h1 {
        font-size: 3.5rem;
    }
</style>
# **Soft Deletes**

---
<!-- _class: lead -->
![w:1000](./../images/thank-you.png)