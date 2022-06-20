package com.projetspring.meriem;

import java.util.Random;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.CommandLineRunner;
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.data.rest.core.config.RepositoryRestConfiguration;

import com.projetspring.meriem.entities.Category;

import net.bytebuddy.utility.RandomString;

@SpringBootApplication
public class EcommerceBackendApplication implements CommandLineRunner{
	  @Autowired
	    private com.projetspring.meriem.dao.ProductRepository productRepository;
	    @Autowired
	    private com.projetspring.meriem.dao.CategoryRepository categoryRepository;
	    @Autowired
	    private RepositoryRestConfiguration repositoryRestConfiguration;
	
	public static void main(String[] args) {
		SpringApplication.run(EcommerceBackendApplication.class, args);
		Category c = new Category();
	
	}

	 @Override
	    public void run(String... args) throws Exception {

	        repositoryRestConfiguration.exposeIdsFor(com.projetspring.meriem.entities.Product.class,Category.class);

	        categoryRepository.save(new Category(null,"Computers",null,null,null));
	        categoryRepository.save(new Category(null,"Printers",null,null,null));
	        categoryRepository.save(new Category(null,"Smart phones",null,null,null));
	        Random rnd=new Random();
	        categoryRepository.findAll().forEach(c->{
	            for (int i = 0; i <10 ; i++) {
	                com.projetspring.meriem.entities.Product p=new com.projetspring.meriem.entities.Product();
	                p.setName(RandomString.make(18));
	                p.setPrice(100+rnd.nextInt(10000));
	                p.setAvailable(rnd.nextBoolean());
	                p.setPromotion(rnd.nextBoolean());
	                p.setSelected(rnd.nextBoolean());
	                p.setCategory(c);
	                p.setImgURL("default.png");
	                productRepository.save(p);
	            }
	        });
	    }

}
