# webpack模块化实现
## commonjs
```javascript
(() => { // webpackBootstrap
	var __webpack_modules__ = {
        // a.js模块
         "./src/a.js": (module) => {

            function sayHello(name) {
                return `Hello ${name}`;
            }
      
            module.exports = sayHello;
     }
   	};
    /************************************************************************/
     	// The module cache
     	var __webpack_module_cache__ = {};
     	
     	// The require function
     	function __webpack_require__(moduleId) {
     		// Check if module is in cache
     		var cachedModule = __webpack_module_cache__[moduleId];
     		if (cachedModule !== undefined) {
     			return cachedModule.exports;
     		}
     		// Create a new module (and put it into the cache)
     		var module = __webpack_module_cache__[moduleId] = {
     			// no module.id needed
     			// no module.loaded needed
     			exports: {}
     		};
     	
     		// Execute the module function
     		__webpack_modules__[moduleId](module, module.exports, __webpack_require__);
     	
     		// Return the exports of the module
     		return module.exports;
     	}
     	
    /************************************************************************/
    var __webpack_exports__ = {};
    // This entry need to be wrapped in an IIFE because it need to be isolated against other modules in the chunk.
    (() => {
    /*!**********************!*\
      !*** ./src/index.js ***!
      \**********************/
    const sayHello = __webpack_require__(/*! ./a */ "./src/a.js");
    
    console.log(sayHello, sayHello('Gopal'));
    })();
    
})();
```
## es6
```javascript
 (() => { // webpackBootstrap
 	"use strict";
 	var __webpack_modules__ = ({

 "./src/a.js": ((__unused_webpack_module, __webpack_exports__, __webpack_require__) => {

    __webpack_require__.r(__webpack_exports__);
    // 和commonjs的主要区别在这里，到下面看方法定义
     __webpack_require__.d(__webpack_exports__, {
       "default": () => (__WEBPACK_DEFAULT_EXPORT__)
     });
    function sayHello(name) {
        return `Hello ${name}`;
      }
      
     const __WEBPACK_DEFAULT_EXPORT__ = (sayHello);
    
    
     })
    
});
    /************************************************************************/
     	// The module cache
     	var __webpack_module_cache__ = {};
     	
     	// The require function
     	function __webpack_require__(moduleId) {
     		// Check if module is in cache
     		var cachedModule = __webpack_module_cache__[moduleId];
     		if (cachedModule !== undefined) {
     			return cachedModule.exports;
     		}
     		// Create a new module (and put it into the cache)
     		var module = __webpack_module_cache__[moduleId] = {
     			// no module.id needed
     			// no module.loaded needed
     			exports: {}
     		};
     	
     		// Execute the module function
     		__webpack_modules__[moduleId](module, module.exports, __webpack_require__);
     	
     		// Return the exports of the module
     		return module.exports;
     	}
     	
    /************************************************************************/
     	/* webpack/runtime/define property getters */
     	(() => {
     		// define getter functions for harmony exports
     		__webpack_require__.d = (exports, definition) => {
     			for(var key in definition) {
     				if(__webpack_require__.o(definition, key) && !__webpack_require__.o(exports, key)) {
                        // 通过Object.defineProperty自定义get,通过函数返回，每次返回都会返回作用域的最新值，也就是输出的是值的引用
     					Object.defineProperty(exports, key, { enumerable: true, get: definition[key] });
     				}
     			}
     		};
     	})();
     	
     	/* webpack/runtime/hasOwnProperty shorthand */
     	(() => {
     		__webpack_require__.o = (obj, prop) => (Object.prototype.hasOwnProperty.call(obj, prop))
     	})();
     	
     	/* webpack/runtime/make namespace object */
     	(() => {
     		// define __esModule on exports
     		__webpack_require__.r = (exports) => {
     			if(typeof Symbol !== 'undefined' && Symbol.toStringTag) {
     				Object.defineProperty(exports, Symbol.toStringTag, { value: 'Module' });
     			}
     			Object.defineProperty(exports, '__esModule', { value: true });
     		};
     	})();
     	
    /************************************************************************/
    var __webpack_exports__ = {};
    // This entry need to be wrapped in an IIFE because it need to be isolated against other modules in the chunk.
    (() => {
    /*!**********************!*\
      !*** ./src/index.js ***!
      \**********************/
    __webpack_require__.r(__webpack_exports__);
    /* harmony import */ var _a__WEBPACK_IMPORTED_MODULE_0__ = __webpack_require__(/*! ./a */ "./src/a.js");
    
    
    console.log(_a__WEBPACK_IMPORTED_MODULE_0__["default"], (0,_a__WEBPACK_IMPORTED_MODULE_0__["default"])('Gopal'));
    })();
    
     })()
    ;
```