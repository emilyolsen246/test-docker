FROM node:8-alpine
FROM rocker/verse:4.0.2
WORKDIR /home/Downloads/example_report
RUN R -e "install.packages(c( \
    'tidyverse', \
    'dotenv', \
    'REDCapR', \
    'knitr', \
    'kableExtra'))"
Run R -e "devtools::source_url('https://raw.githubusercontent.com/ctsit/r_utils/master/install_latex_packages.R')"
ADD test_format.Rmd /home/Downloads/example_report/test_format.Rmd
ADD targets.csv /home/Downloads/example_report/targets.csv
ADD oneflorida.png /home/Downloads/example_report/oneflorida.png
ADD *.Rmd /home/Downloads/example_report/
RUN mkdir /test-source
COPY test_format.Rmd /test-source/
COPY targets.csv /test-source/
COPY oneflorida.png /test-source/
COPY *.Rmd /test-source/
CMD ["R", "-e", "rmarkdown::render('/test-source/test_format.Rmd', output_file='/home/Downloads/example_report/test_format.pdf')"]
