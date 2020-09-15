
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
