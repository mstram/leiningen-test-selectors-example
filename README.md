leiningen-test-selectors-example
================================

   lein new app t1

 test/t1/core_test.clj
 
   (deftest ^:integration network-heavy-test
       (is (= [1 2 3] (:numbers (network-operation)))))
                       
   (deftest ^:integration network-medium-test
       (is (= [4 5 6] (:numbers (network-operation)))))
       
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
