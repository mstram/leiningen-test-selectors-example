leiningen-test-selectors-example
================================

```clojure
   lein new app t1
```
 test/t1/core_test.clj
 
 
 ```clojure
 
 (ns a1.core-test
  (:require [clojure.test :refer :all]
            [a1.core :refer :all]))


(defn network-operation []
 (prn "(network-operation)")
 {:numbers [1 2 3] :extras "whatever"})
 
 
 (deftest ^:integration network-heavy-test
     (is (= [1 2 3] (:numbers (network-operation)))))
                       
 (deftest ^:integration network-medium-test
       (is (= [4 5 6] (:numbers (network-operation)))))
 
 (deftest ^:integration network-heavy-test2
  (prn "network-heavy-test2")
   (let [ x  (:numbers (network-operation2) )]
       (prn "x: " x  " (type x) : " (type x))
       (prn "(x 0) " (x 0) )))

    ;;
    ;; these are ignored by  `lein test :integration`
    ;;
 
    (deftest ^:otherTag  test1
     (prn "--- test1 ---")
     (testing "(test1)FIXME, I fail."
     (is
       (= 0 1))))
       
       
    (deftest  test-no-tag   ;; no tag
     (prn "--- test-no-tag ---")
     (testing "(test-no-tag)FIXME, I fail."
     (is
       (= 0 1))))
       
        
  lein test                ;runs all tests
  
  lein test :integration   ; runs only tests tagged with ^:integration
  
```
From lein repl
==============

```
  lein repl
  
 (require '[clojure.test :refer [run-tests]])
 (require 't1.core-test)
 (run-tests 't1.core-test)
 
 

