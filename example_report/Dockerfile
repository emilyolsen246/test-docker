FROM rocker/verse:4.0.2
WORKDIR /home/Downloads/example_report
RUN R -e "install.packages(c( \
    'tidyverse', \
    'dotenv', \
    'REDCapR', \
    'knitr', \
    'kableExtra'))"
ADD test_format.Rmd /home/Downloads/example_report/test_format.Rmd
ADD targets.csv /home/Downloads/example_report/targets.csv
ADD oneflorida.png /home/Downloads/example_report/oneflorida.png
ADD *.Rmd /home/Downloads/example_report/
CMD ["R", "-e", "rmarkdown::render('/home/Downloads/example_report/test_format.Rmd', output_file='/newfolder/test_format.pdf')"]
COPY home/Downloads/test_format.pdf /home/Downloads/example_report/test_format.pdf