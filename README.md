# preparation work
This is the version of Humaneval-X that uses openkey_API, and therefore relies on the original codegeex for evaluation. This is accomplished by replacing the humaneval-x folder in codegeex.

```
$ git clone https://github.com/THUDM/CodeGeeX
$ conda create -n HEX python=3.8
$ conda activate HEX
$ pip install -e .
$ cd codegeex/benchmark
$ rm -r humaneval-x
$ git clone https://github.com/Qlalq/humaneval-x
```

# Usage
## Answer Generation
Fill in the **openai.api_key** and change the **language** parameter (default is cpp) to select a library in **gen_samples.py**,Run gen_samples.py

``$ python gen_samples.py``

The sample results are stored in a folder, similar to the following folder:js/data/samples_js.jsonl

## Evaluation of results
Cpp and python can be evaluated normally, but js, java, go need to install the corresponding language compiler separately
```
$python evaluate_humaneval_x.py --n_workers 64 --problem_file humaneval-x/cpp/data/humaneval_cpp.jsonl.gz --input_file humaneval-x/cpp/data/samples_cpp_GPT4o.jsonl --out_dir humaneval-x/cpp/data/ --timeout 5
$python evaluate_humaneval_x.py --n_workers 64 --problem_file humaneval-x/go/data/humaneval_go.jsonl.gz --input_file humaneval-x/go/data/samples_go.jsonl --out_dir humaneval-x/go/data/ --timeout 5
$python evaluate_humaneval_x.py --n_workers 64 --problem_file humaneval-x/java/data/humaneval_java.jsonl.gz --input_file humaneval-x/java/data/samples_java.jsonl --out_dir humaneval-x/java/data/ --timeout 5
$python evaluate_humaneval_x.py --n_workers 64 --problem_file humaneval-x/python/data/humaneval_python.jsonl.gz --input_file humaneval-x/python/data/samples_python.jsonl --out_dir humaneval-x/python/data/ --timeout 5
$python evaluate_humaneval_x.py --n_workers 64 --problem_file humaneval-x/js/data/humaneval_js.jsonl.gz --input_file humaneval-x/js/data/samples_js.jsonl --out_dir humaneval-x/js/data/ --timeout 5
```

## Sample Error Summary
``$ python false.py``