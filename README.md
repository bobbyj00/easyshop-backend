EasyShop Backend
This is the backend API for EasyShop, a simple e-commerce application built with Spring Boot and MySQL.

The API supports user registration, login, product browsing, category management, and product CRUD operations. It demonstrates clean RESTful design and role-based access control.

Features
User registration & login with JWT authentication
Category CRUD (only admins can modify categories)
Product CRUD with filtering and searching
Simple, maintainable codebase ready for extension
Example Code Snippets
1. Category Controller - Role-based Access Control
@RestController
@RequestMapping("/categories")
public class CategoriesController {

    @GetMapping
    public List<Category> getAll() {
        return categoryDao.findAll();
    }

    @PostMapping
    @PreAuthorize("hasRole('ADMIN')")
    public Category create(@RequestBody Category category) {
        return categoryDao.create(category);
    }

}
