# Parallel Inheritance Hierarchies

`Parallel Inheritance Hierarchies` merupakan code smell yang terjadi ketika ada hierarki kelas yang sejajar dan terpisah yang seringkali ditambah/dikembangkan secara bersamaan. Dalam konteks ini, `parallel` merujuk pada hierarki yang sejajar satu sama lain, sementara `inheritance` menunjukkan bahwa hierarki tersebut dibangun melalui pewarisan kelas.

### Contoh

Berikut adalah contoh dari `Parallel Inheritance Hierarchies` :

```java
public interface AreaInterface {
	public float area();
}
```
```java
public abstract class Shape2D {
	protected float width;
	protected float height;

	public float getWidth() {
		return width;
	}

	public void setWidth(float width) {
		this.width = width;
	}

	public float getHeight() {
		return height;
	}

	public void setHeight(float height) {
		this.height = height;
	}
}
```

Penjelasan

### Perbaikan

Penjelasan

Berikut adalah hasil refactor

```java
public interface AreaInterface {
	public float area();
}
```
```java
public abstract class Shape2D implements AreaInterface {
	protected float width;
	protected float height;

	public float getWidth() {
		return width;
	}

	public void setWidth(float width) {
		this.width = width;
	}

	public float getHeight() {
		return height;
	}

	public void setHeight(float height) {
		this.height = height;
	}
}
```

[Back to Home Page](https://jonathanchr1.github.io/code-re/)
