# hse_hw1_meth
- https://colab.research.google.com/drive/1tkgOsiHW6YoBSKL4g12TeDI4UDzVlSL7?usp=sharing
- Сколько ридов пришлось на целевые регионы?

| Образец | chr11:58717111-58917111 | chr11:40185800-40195800 |
| --- | --- | --- |
| 8 Cell | 2744 | 464 |
| ICM | 5060 | 630 |
| Epiblast | 8935 | 1062 |
- Сколько дуплицированных чтений в каждом образце?

| Образец | Число дуплицированных чтений | Процент дуплицированных чтений |
| --- | --- | --- |
| 8 Cell | 521904 | 18.31% |
| ICM | 377882 | 9.08% |
| Epiblast | 205258 | 2.92% |
- Параллельное дедуплицирование:
```
#!/bin/bash

deduplicate_bismark --bam --paired -o s_8_cell SRR5836473_1_bismark_bt2_pe.bam &
deduplicate_bismark --bam --paired -o s_ICM SRR5836475_1_bismark_bt2_pe.bam &
deduplicate_bismark --bam --paired -o s_epiblast SRR3824222_1_bismark_bt2_pe.bam &
wait
```
### M-Bias:
- 8cell
![](https://github.com/sashkent3/hse_hw1_meth/raw/main/images/8cell_mbias.png)
- ICM
![](https://github.com/sashkent3/hse_hw1_meth/raw/main/images/ICM_mbias.png)
- epiblast
![](https://github.com/sashkent3/hse_hw1_meth/raw/main/images/epiblast_mbias.png)
### Гистограммы распределения метилирования цитозинов по хромосоме
![](https://github.com/sashkent3/hse_hw1_meth/raw/main/images/8cell_hist.png)
![](https://github.com/sashkent3/hse_hw1_meth/raw/main/images/ICM_hist.png)
![](https://github.com/sashkent3/hse_hw1_meth/raw/main/images/epiblast_hist.png)

__Выводы:__ В целом распределение метилирования цитозинов совпадает с указанным в приведенной статье. Действительно, на стадии ICM можно наблюдать пик гистограммы в нуле, в то время как у epiblast наоборот большинство попало в 100%. Cell8 можно охарактеризовать промежуточным результатом: здесь четко выделяется и пик в нуле, и пик у 100%.

### Уровень метилирования
![](https://github.com/sashkent3/hse_hw1_meth/raw/main/images/image_meth.png)
### Уровень покрытия
![](https://github.com/sashkent3/hse_hw1_meth/raw/main/images/image_cov.png)
