# SpringBlog-WebService

> Service Oriented Architecture

> WS --> Protocole de communication entre plusieurs application

>Standard SOAP
>Standard REST

Utilisation du protocole HTTP
	...
	...
	...
	
	
## I - Creation du Web Service dans le controller
 
> Creation du fichier ArticleWebService	

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
	
	