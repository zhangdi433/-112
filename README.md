
让我们对自己的代码有信心。
如果修改一个功能如果没有任何测试代码，只能靠接口测试，当业务逻辑相对简单的时候可能还比较可行，但当业务逻辑非常复杂流程很长的时候，可能一个很小的代码错误就会让这次精心设计的测试场景泡汤，又得重新来过，而这个很小的代码错误在跑整个流程之前可以通过一个简单的单元测试发现。如果没有单元测试，长此以往，我们总是觉得自己的代码可能有问题，但是又无从检查，如果修改多次仍然有问题，慢慢地就失去了耐心和信心。
让BUG发现的时间提前。
测试时会将一些边界条件作为测试用例，而这些边界条件在实际使用中可能会很晚才发现，到时候程序异常出现BUG，改动起来一定会比一开始就发现这些问题更费时间。如果基于TDD的模式开发，一些代码逻辑的BUG、边界条件的疏忽问题都会提前得到解决。
为代码重构保驾护航。
重构代码和重写代码的重要区别是：重写可能导致系统暂时不可用，但重构系统一定是随时可用的，那怎么保证重构过程中系统功能不受影响呢？单元测试可以为重构提供一定的帮助，如果我们用提取函数的手法重构了一段代码，直接跑原有的测试用例就可以保证重构没有破坏原来的逻辑结构。
通过单元测试快速熟悉代码。
单元测试中的用例可以说是一种很好的文档，通过查看单元测试可以很快了解代码逻辑，特别是一些边界条件和历史bug。
优化设计。
编写单元测试驱动开发从调用者的角度去设计代码，让代码易于调用和测试，特别是使用TDD测试驱动开发的方式，开发者会在开发中不断调整和重构，让代码有一个较好的结构和设计，并解除软件中的耦合。
可快速持续回归。
结合持续集成，任何代码的修改都可以快速回归，而不是需要通过接口测试覆盖可能修改的路径，后者太麻烦不知能，也不一定每次都能覆盖所有路径
package Test;

public class test_1 {
	public static void main(String[] args) {
		int[] chengji = {-1, -15, -5586, 5956,100,95,48,85,6,21,35,48,78,96,25};
     	printArr(chengji);
		bubbleArray(chengji);
		System.out.println();
		printArr(chengji);
//		System.out.print(chengji);
	}
		private static void printArr(int[] chengji) {
			for(int i = 0 ; i< chengji.length ; i++) {
				 System.out.print(chengji[i]+ " ");
			}
		}
	
	
	public static String printArray(int[] chengji) {
		String s = "";
		for(int i = 0 ; i< chengji.length ; i++) {
			 String.join(s, chengji[i]+ " ");
		}
		return s ;
	}
	
	public static void bubbleArray(int chengji[]) {
		for(int i = 0; i<chengji.length-1 ;i++) {
			for(int j = 0;j<chengji.length - i -1 ;j++) {
				if(chengji[j]>chengji[j+1]) {
					int temp = chengji[j];
					chengji[j] = chengji[j+1];
					chengji[j+1] = temp ;
				}
			}
		}
	}
  package Test;

import static org.junit.Assert.*;

import org.junit.Test;

public class Test {

	@Test
	public void testBubbleArray1() {
		int[] arr1 = {100,95,99,84,26,78,96,25};
		int[] arrend = {25,26,78,84,95,96,99,100};
		test_1.bubbleArray(arr1);
		test_1.printArray(arr1);
		assertTrue(test_1.printArray(arr1).equals(test_1.printArray(arrend)));
				
	}

	@Test
	public void testBubbleArray2() {
		int[] arr2 = {100,95,99,15,43,35,48,78,96,25};
		int[] arrend = {15, 25, 35 ,43 ,48, 78, 95, 96, 99, 100};
		test_1.bubbleArray(arr2);
		test_1.printArray(arr2);
		assertTrue(test_1.printArray(arr2).equals(test_1.printArray(arrend)));
		
	}

	@Test
	public void testBubbleArray3() {
		int[] arr3 = {100,95,25};
		int[] arrend = {25,95,100};
		test_1.bubbleArray(arr3);
		test_1.printArray(arr3);
		assertTrue(test_1.printArray(arr3).equals(test_1.printArray(arrend)));
		
	}

	@Test
	public void testBubbleArray4() {
		int[] arr4 = {100,95,95,95,96,96,25};
		int[] arrend = {25 ,95 ,95, 95, 96, 96,100};
		test_1.bubbleArray(arr4);
		test_1.printArray(arr4);
		assertTrue(test_1.printArray(arr4).equals(test_1.printArray(arrend)));
		
	}

	@Test
	public void testBubbleArray5() {
		int[] arr5 = {-1, -15, -5586, 5956,100,95,99,84,26,48,85,6,21,35,48,78,96,25};
		int[] arrend = {-5586, -15 ,-1 ,6 ,21 ,25 ,26 ,35 ,48 ,48, 78 ,84 ,85 ,95 ,96 ,99 ,100 ,5956};
		test_1.bubbleArray(arr5);
		test_1.printArray(arr5);
		assertTrue(test_1.printArray(arr5).equals(test_1.printArray(arrend)));
		
	}
