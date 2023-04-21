# Lab-8_202001461
## Name : Harsh Agheda
## ID : 202001461

## 1. Created a new Eclipse project, inside the project created a package and definined the class
![233036757-48d69020-3270-44bc-9c8b-c8443862f8ff](https://user-images.githubusercontent.com/84801162/233594900-a14ef0f8-aa2f-4482-a502-9b7571166c0b.png)

### 2. Test method to test the behaviour of the Boa class : 
```
import org.junit.Assert;
import org.junit.Test;
public class BoaTest {
  @Test
  public void testIsHealthy() {
    Boa healthyBoa = new Boa("Lucy", 8, "granola bars");
    Assert.assertTrue(healthyBoa.isHealthy());
    
    Boa sickBoa = new Boa("Sneaky", 6, "mice");
    Assert.assertFalse(sickBoa.isHealthy());
  }
  @Test
  public void testFitsInCage() {
    Boa smallBoa = new Boa("Tiny", 2, "rats");
    Assert.assertTrue(smallBoa.fitsInCage(5));
    Assert.assertFalse(smallBoa.fitsInCage(1));
    Boa largeBoa = new Boa("Goliath", 20, "chicken");
    Assert.assertTrue(largeBoa.fitsInCage(25));
    Assert.assertFalse(largeBoa.fitsInCage(10));
  }
}
```
![233039273-d00304f8-2deb-4061-af0c-b76a2254d573](https://user-images.githubusercontent.com/84801162/233598261-b9dfd442-0336-40d2-b484-7a1fb1828ea9.png)
</br>

### 3. Modified setUp() method in the BoaTest class : 
```
public class BoaTest {
    private Boa jen;
    private Boa ken;
    
    @Before
    public void setUp() throws Exception {
        jen = new Boa("Jennifer", 2, "grapes");
        ken = new Boa("Kenneth", 3, "granola bars");
    }
    
    // write test methods here
}
```
![image](https://user-images.githubusercontent.com/84801162/233598931-8202d0d3-9024-4811-95a8-76c8b9d8d32f.png)
</br>

### 4. Modified testIsHealthy() method in the BoaTest class : 
```
@Test
public void testIsHealthy() {
    // check that jen is not healthy
    assertFalse(jen.isHealthy());
    
    // check that ken is healthy
    assertTrue(ken.isHealthy());
}
```
</br>

### 5. Modified testFitsInCage() method in the BoaTest class : 
```
@Test
public void testFitsInCage() {
    // Test for jen
    assertFalse(jen.fitsInCage(1)); // cage length is less than length of boa
    assertTrue(jen.fitsInCage(2)); // cage length is equal to length of boa
    assertTrue(jen.fitsInCage(3)); // cage length is greater than length of boa
    // Test for ken
    assertFalse(ken.fitsInCage(2)); // cage length is less than length of boa
    assertTrue(ken.fitsInCage(3)); // cage length is equal to length of boa
    assertTrue(ken.fitsInCage(4)); // cage length is greater than length of boa
}
```
</br>

### 6. Run tests
![image](https://user-images.githubusercontent.com/84801162/233599151-fd7a153d-08ca-4de9-8261-efda1f15e95e.png)

### 7. Modified Boa class with new lengthInInches() method:
```
public class Boa {
    private String name;
    private int length; // the length of the boa, in feet
    private String favoriteFood;
    public Boa(String name, int length, String favoriteFood) {
        this.name = name;
        this.length = length;
        this.favoriteFood = favoriteFood;
    }
    // returns true if this boa constrictor is healthy
    public boolean isHealthy() {
        return this.favoriteFood.equals("granola bars");
    }
    // returns true if the length of this boa constrictor is
    // less than the given cage length
    public boolean fitsInCage(int cageLength) {
        return this.length < cageLength;
    }
    // produces the length of the Boa in inches
    public int lengthInInches() {
        return this.length * 12;
    }
}
```
### 8. Test for lengthInInches() method:
```
import static org.junit.Assert.assertEquals;
import org.junit.Before;
import org.junit.Test;
public class BoaTest {
    private Boa jen;
    private Boa ken;
    @Before
    public void setUp() throws Exception {
        jen = new Boa("Jennifer", 2, "grapes");
        ken = new Boa("Kenneth", 3, "granola bars");
    }
    @Test
    public void testLengthInInches() {
        assertEquals(24, jen.lengthInInches());
        assertEquals(36, ken.lengthInInches());
    }
}
```
This new test case verifies that each of the Boa objects created in the setUp() function returns the expected value when the lengthInInches() method is called on it. The expected number and the actual value returned by the lengthInInches() method are compared using the assertEquals() method. The @Test annotation indicates that this is a test method that should be run by JUnit.
</br>
