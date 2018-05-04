# SpringBlog-WebService

point de depart  le projet SpringBlog <br>
-  https://github.com/TarikMann/SpringBlog.git

Source : 
- https://mvnrepository.com/

> Service Oriented Architecture

> WS --> Protocole de communication entre plusieurs application

>Standard SOAP
>Standard REST

Utilisation du protocole HTTP
	...
	...
	...
	
	
## I - Creation du Web Service dans le controller
 
### 1 - Creation du fichier ArticleWebService	

	@RestController
	@RequestMapping("/api/article")
	public class ArticleWebService {

		@PostMapping({ "", "/" })
		Article create(@RequestBody Article article) {
			return null;
		}

		@GetMapping("/{articleId}")
		Article read(@PathVariable Integer articleId) {
			return null;
		}

		@PutMapping("/{articleId}")
		Article update(@PathVariable Integer articleId, @RequestBody Article article) {
			return null;
		}

		@DeleteMapping("/{articleId}")
		@ResponseStatus(code = HttpStatus.NO_CONTENT)
		void delete(@PathVariable Integer articleId, @RequestBody Article article) {

		}

	}

> Ne pas oublier la liste de tous les articles .

	...
	@GetMapping({ "", "/" })
	List<Article> list() {
		return null;
	}
	....

	
> Ajouter l'annotation Autowired et l'articleRepository
	
	@Autowired
	private ArticleRepository articleRepoditory;

### 2 - Delete

	@DeleteMapping("/{articleId}")
	@ResponseStatus(code = HttpStatus.NO_CONTENT)
	void delete(@PathVariable Integer articleId) {
		this.articleRepoditory.deleteById(articleId);
	}

### 3 - La liste des articles

	@GetMapping({ "", "/" })
	List<Article> list() {
		return this.articleRepoditory.findAll();
	}

### 4 - Le read

	@GetMapping("/{articleId}")
	Article read(@PathVariable Integer articleId) {
		return this.articleRepoditory.getOne(articleId);
	}

### 5 - Update

	@PutMapping("/{articleId}")
	Article update(@PathVariable Integer articleId, @RequestBody Article article) {
		return this.articleRepoditory.save(article);
	}


### 6 - Create

	@PostMapping({ "", "/" })
	Article create(@RequestBody Article article) {
		return this.articleRepoditory.save(article);
	}

## II- Ajouter les dependances Maven

	<!-- https://mvnrepository.com/artifact/com.fasterxml.jackson.core/jackson-databind -->
	<dependency>
		<groupId>com.fasterxml.jackson.core</groupId>
		<artifactId>jackson-databind</artifactId>
		<version>2.9.5</version>
	</dependency>

## III - 



## IV - On teste notre WebService

> Pour voir Si notre webservice fonctionne on test l'url suivante :
 
- http://localhost:8080/SpringBlog-WebService/api/article

> on affiche un fichier Json



