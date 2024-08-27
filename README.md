# Laboratory-Exercise-2-Data-Abstraction-By-Group-package 

LibraryManagementSystem;
public class ArrayList<T> {
   private T[] array;
   private int size;
   @SuppressWarnings("unchecked")
   public ArrayList() {
       array = (T[]) new Object[10];  // Initial capacity
       size = 0;
   }
   public void add(T element) {
       ensureCapacity();
       array[size++] = element;
   }
   public void insert(int index, T element) {
       if (index < 0 || index > size) {
           throw new IndexOutOfBoundsException("Invalid index");
       }
       ensureCapacity();
       for (int i = size; i > index; i--) {
           array[i] = array[i - 1];
       }
       array[index] = element;
       size++;
   }
   public T remove(int index) {
       if (index < 0 || index >= size) {
           throw new IndexOutOfBoundsException("Invalid index");
       }
       T removedElement = array[index];
       for (int i = index; i < size - 1; i++) {
           array[i] = array[i + 1];
       }
       array[--size] = null;
       return removedElement;
   }
   public T get(int index) {
       if (index < 0 || index >= size) {
           throw new IndexOutOfBoundsException("Invalid index");
       }
       return array[index];
   }
   public int size() {
       return size;
   }
   public boolean isEmpty() {
       return size == 0;
   }
   @SuppressWarnings("unchecked")
   private void ensureCapacity() {
       if (size == array.length) {
           T[] newArray = (T[]) new Object[array.length * 2];
           System.arraycopy(array, 0, newArray, 0, array.length);
           array = newArray;
       }
   }
}
