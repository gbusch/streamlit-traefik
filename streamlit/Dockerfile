FROM python:3.12-slim

# streamlit-specific commands
RUN mkdir -p /root/.streamlit
RUN bash -c 'echo -e "\
[server]\n\
enableCORS = false\n\
" > /root/.streamlit/config.toml'

COPY ./streamlit/requirements.txt /root
COPY ./streamlit/src /root/src
RUN pip3 install -r /root/requirements.txt