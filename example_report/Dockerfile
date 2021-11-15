# two different base images
FROM node:8-alpine

FROM rocker/verse:4.0.2

# specifies execution from the example_report folder
WORKDIR /home/Downloads/example_report

# install necessary libraries
RUN R -e "install.packages(c( \
    'tidyverse', \
    'dotenv', \
    'REDCapR', \
    'knitr', \
    'kableExtra'))"

# installs latex package from devtools
Run R -e "devtools::source_url('https://raw.githubusercontent.com/ctsit/r_utils/master/install_latex_packages.R')"

# adds files from example_report
ADD test_format.Rmd /home/Downloads/example_report/test_format.Rmd
ADD targets.csv /home/Downloads/example_report/targets.csv
ADD oneflorida.png /home/Downloads/example_report/oneflorida.png
ADD *.Rmd /home/Downloads/example_report/

# creates a new input directory
RUN mkdir /test-source

# copy files to the new input directory
COPY test_format.Rmd /test-source/
COPY targets.csv /test-source/
COPY oneflorida.png /test-source/
COPY *.Rmd /test-source/

# makes a target folder for output
RUN mkdir /home/output

# executes and outputs a pdf file into the target output directory based off of info from the input directory
CMD ["R", "-e", "rmarkdown::render('/test-source/test_format.Rmd', output_file='test_format.pdf', output_dir='/home/output')"]
