My understanding of the exercise is to provide a step by step documentation for a potential Datadog customer or client to follow. I don’t know the client base of Datadog and so I cannot guess the technical skills of an average client. I am also not an experienced system administrator myself and I don’t necessarily comprehend the significance of each function I used in Datadog. I don’t know the terminology used and prefered by Datadog.  As such I don’t think I can provide a documentation that would serve the best interest of any potential Datadog client.  

## Shotcuts
[Prerequisites - Setup the environment](#prerequisites-setup-the-environment)

[Collecting Metrics](#collecting-metrics)

[Visualizing Data](#visualizing-data)

[Monitoring Data](#monitoring-data)

[Collecting APM Data](#collecting-apm-data)

[Final Question](final-question)

# Prerequisites: Setup the environment 
The installation of the Datadog Agent on my virtual machine returned an error. I followed the link provided in the message for additional troubleshooting steps.  There was not much additional information available to troubleshoot my error in the documentation. As a customer I would be very much annoyed if I was directed to a page to find no relevant information available. The second time I run the install commands it went through with the installation.

![Install error](https://lh3.googleusercontent.com/F8CqK2pOnMNdJk_UFANppslYT6f35K8a_dlEHvXfkuqSu9Rqihu4z2NEhxZhQqDfcvIsTpJmG1_dZjvkDXTP0IteVKA-l85gtKpMugmxaLQuUh_M9-CWs6Bc3OxPeo6kGU5o73aadBNcO3nJMTKDIfWcevf3p352s6HqfsTqtzu8neVJMb6wH6qGLXiaQZceQyyqhsT0h98nMa20wocc3v0cb6yn14TOkgQqwl4Ni7PDJ_ZAsTL--QBzQ7ZYrU6rzBa_NI1vCoHEuNhynMF06ibrF5Y-0qF4g-MfZs0ujH45iTfhlpGk29mAJuSYCiD_nl_flOtl-X6PWafbte_N1yZmP8LdlJFtKdurlkxjYUh3zbjjcYGq0c1IxZU9VY-24CFKiL3L8DOyM6XMxYxG1UF95eluTTc2fsn6CXX_J7q58jEol_L8vFsP-vAQQGjVE0MlOdGmpRRo2T1pjl2m5VOnssAB16cE-9-2KWjefmv0opgDO3iyzdxjC5FHGUgSKloDdnOUbImNg6P2QkxSanNxe82_-P4bpsghfbttHPZdMl71QZMKO5ORuJ_TLbzHTh_BxeHmx86BtyfCZO02bhN0pIl6P-s5qnftcmEYsWU=w1193-h452-no)

# Collecting Metrics

## Add tags in the Agent config file and show us a screenshot of your host and its tags on the Host Map page in Datadog.

In this step we are going to assign tags to each hosts in our environment. This step is optional but we highly recommend using tags for a better experience. Host Tags will automatically be added to that host's metrics and events, metrics can be filtered and aggregated by Tag. 

You have the option to assign key:value pairs. The key can be region, database, role, env and tags. A good example would be: *region:nsw, application:database, database:primary, tags: test, ubuntu*.

1. Open the */etc/dd-agent/datadog.conf* file with a text editor. Make sure you have write permission on the file. 
2. Navigate to the *# Set the host's tags (optional)*
3. Remove the comment and type in your preferred tags. Example:  *tags: ubuntu, virtual, env:prod, role:testrun*
4. Save the modifications to the file. 
5. Restart your Datadog Agent with *sudo service datadog-agent restart*.
6. You can verify your new tags by logging into your Datadog instance: https://app.datadoghq.com
7. From the menu in the left hand side select Infrastructure,  Infrastructure List. 
8. Hover over the the host name and click on inspect. 
9. You should see the new tags on the top half of the popup window.


Tags on Infrastructure List | Tags on Host Map
----|----
![](https://lh3.googleusercontent.com/Se_YE9W7Lt8Jxdwdjr4qV1sdXUdkh9sz6DWK9-2W1MKEIeT7gHjRIlEyQxFgQFV48SKuQLcBWbgBsug7ai2MFLIHWAEFmINrn9LGaa9r4hlq6l1cgxCEzj7qXgleND5qZtilH9vwHsCUlyntel1X2-YcPrF1jCRe4z57yPqvd6roN_cS1cDrBbNiyS3e0Pz3k2iHglnZfleEbE6kexuCIjMJurCb1qzvqYKrWWgStnT1_4d_ZDZ4MbGganmoZhA9tLJwf9Fg0kQn-9uAlJ04elKjGpivmcqQ9tDnVGkW6-2pfW-D8HAjpe03XXrhwNFq9ksauFAekeynxtmey66zEYq2IDAV-kh00Pq7cn4AqJaZ3XiGa-xU2DJh1nuHR3J1csBp4guD7LzJETdyFjo1QBbfes2r-bpNhnBm_LKob67zB5L2fJzQRgZxkhOHqpOnzLszUbtn_yLk_nv7LHAGFbgmPsj093fLnlV7XUCZHiBm-avmqNfgeIGzuU97TAn4FZD03aFC87ACquL4iOhupxZN0na3wbqzhzoayPbMGbkkTtJuqYcfw_FlY7oD6N661SGlShpkMZBgEuHlNmfbLHiJfsFdq4rJbXGGdotLym4=w1092-h599-no) | ![](https://lh3.googleusercontent.com/d7Kxi44-1JTtPyC2Xis4lTgrxaJMQ-xdNbm2wciIobhbHbT3tpM4gZF3C1Moa271F0VtjhwLzMH-IZgEk3vkxPkbc26o94-2Su6iXPm-_WDeQ6AJorm2R9cPTE7ImK3Lv4EZqk0IgcELeXt46aWkJa4rnAHRPAyM0qrIT1mN4anacqEs5G6VnjjzGq4MbF56FPWOLBlgQ6qkKinmOVMhp8Ne1r5X6JR_UnAsCZBWdevUD6TqDCviXKkIslvZxARj4EIgxNSVax9ib3kBkQGZC60OMg9016Nu6UJ8jVDclPYTMeVJYazqe8rW5nrl1SFMr_SjJDV2aE0FtEhe5XH8xOiWUMwEwzUNByemnNuH0GqVQIWB_LDS-TPNZuchzyUcLn4MZhb6KdS1_2PvomgCI61NnioEvwn6zNqbWm_avJrtjB0yGE9r8ULSWwFTUtQoDLHjH_2vPrI3Vrb8lI6M_ncd7fvmAU5b1s2EQVwBm4Y4RN8Dapf-P_hkMUkiQAWQEUftOSXROdbwb6sjmN0RRlOWlnawrTXqdL97ioTHSDyYMjury3m7k933fWeU9jUpS9u23jOpzryHQEApE0zAvmWesE-WdT9mi8V4iGDGjLE=w1079-h616-no)

You can learn more about tags and their uses by navigating here: https://docs.datadoghq.com/guides/tagging/

 ## Install a database on your machine (MongoDB, MySQL, or PostgreSQL) and then install the respective Datadog integration for that database.
Datadog offer several ready to use integrations. You can find the full list of available integrations form your Datadog website (https://app.datadoghq.com). You can find the available metrics for each service by clicking on the name of the service and choosing the Metric tab.

Below is a guide to a simple MySQL inetegration.

1. After logging on to the Datadog UI, use the left hand side menu bar to navigate to Integrations and click on Integrations. 
2. Search for the name of the service, or scroll through to find it. 
3. Once you selected MySQL click on the Configuration tab. 
4. You will need to create a datadog user on your MySQL server and assign permissions to it as per your requirements.
5. We implemented a password generator to make copy and paste easier. Once you clicked on the “Generate password” button, it fills the space with a randomly generated, secure password for you to use. ( Please take a closer look of the password and remove any \ from it. The integration can fail if you use a password with \ in it. )
6. Follow the instructions on the Configuration tab to install the integration.
7. After you completed the configuration steps make sure you restart the Agent: *sudo /etc/init.d/datadog-agent restart*
8. You can use the following command to check if your implementation was successful and is sending metrics: *sudo dd-agent info*

![](https://lh3.googleusercontent.com/3UiJYj26oeH6zx1sRu0KYFkj3w_RafI5SREGqqR_2qveJYrIfPdHBLS0dwBpgWNgsv-_kr8m22Ecj4rfVD4SuVUXLUe7p336o5HvHAJHwKzUO9n1EdSlh9SrpplrlKsCEdJU64DiMcx9ed9RDCyIfzh6HJaxLvmWIbD_QBAjkE1k4llkN5-X50Fjna6R3EkBdyBLhIIqyfJ7fyWWygCE9uA4OJ1GxBfC609S2ymPIaHpim4EjDuYdaDlpBf_6DIatBkEtJSz9-u36Epy78ASNedchAWMEP4twyCUrhop5Xh7kBDJaIEKFlQtBfhG4SNkRfFxTc-LuOw1e4xY_31U-c7HR-pW-921oEM8vpJS6CCIWftErKiJ6XNikwqypMrruoa8L8z38c7h9SpI9Q4ifxlUAC6zXtVKIWSYqSWEL_EVMa64fwIzrMHE6ZsWAqpZ6ThSPc0_d_I3ureaE0TptWAHV4nsb1kEDPeo_6v6Bko_CK_1dR1xBkh6K5glDuZl5AJsI6MCG_bN1NrtDgkn0vUil-gGX54bKrY9EVDDFZ7M_Z_TGoIh9iA5msc5SjBs0t2Pp8J5sLYlGW4klYv2ytMrIcyKGGwAs_3iirkRph8=w527-h643-no)

You can start using the user interface to monitor your MySQL server now. It could take up to 5 minutes to see data coming in.

## Create a custom Agent check that submits a metric named my_metric with a random value between 0 and 1000. Change your check's collection interval so that it only submits the metric once every 45 seconds.

Sending your application’s custom metrics to Datadog will let you correlate what’s happening with your application, your users and your system.
To learn more about how to create a custom metrics, click here: https://docs.datadoghq.com/guides/agent_checks/

We are going to save our custom metric code to etc/dd-agent/checks.d/ and its yaml file to /etc/dd-agent/conf.d/. The names of the files you create has to match. 
Below you can see a simple random number generator which submits a random number between 0 and 1000 in every 45 seconds.

To generate your new metric run to create the check: *sudo nano /etc/dd-agent/checks.d/RandomNum.py*

![](https://lh3.googleusercontent.com/H3x2TXdHCYGxZhFDw0PT2pai5ETGt8ERb3GGdeqICUsO9lZTzG5t99MrWru3kwJCZpasGjAz6xM14FISIMb17vQ2bptWYmO_ScLOn-R8HxrNZ5aB5dZL37n52epocorDYd6Xf9sUgFfu_UlFb38ANgYDRfD5PK3V5OnWqg0MkQym3M0fLKrNv8P3P2eUH4NH_nV4t0HWkMAQbC-jF-_TwnGb059ndwxqxIFCXTCWSWrlf1Gdyk33dVquOgKS8SbNYQb3tha7ChkWxmfP063VxE4QD4ITCT66as8vTdJQiMiTVPnECRR4egsWCMv7JtET2pFfVFTpKLoIoIwl_5LSfwwlUknuwfmm8ChVIMI8Zftauo5RxM17CMN8a67fRQ25vgDORpYIp3ncOjLNsiV1SIJougqztcO3mJGGELUu5NGqyOAHnunzbRKB5KTTAlujpQ3qkMuhzVkSZjtp1aju8Ybr1YGXIVcJeLZBZ8ES3-nTuSXT9Yy4F77TOzbGcnl0rCj6EiMobBBnfemw1iksOl_A0rGmpRmqTzf_IKJoPRGxQgX7OGELXk9j701nyLer3j2VGKRB-DMxqp_69EZkRkGlFjolVrRe8CrDBZZK3mg=w501-h135-no)

To create the config file run *sudo nano /etc/dd-agent/conf.d/RandomNum.yaml*

![](https://lh3.googleusercontent.com/jqRgJTriwXTNLp4RmP80oIl3idJVbnLu4vR9oAotFVMc41ICgQDzjx6m3qnBR9I5xHIC2JV0td68TNcWihuC0-ZuDGuigdazvUjccguCoZwzEoEq0ccFS-z6du_uezTYSej4mTy9c8-bQqgjPT5sxECyON3BttOrMppuyl-PKSfwY2uycD7TqulLggmzlMXcnHHUnuZpcBgsZRDpgoE33aL8b1dDsWOXhaROMKqpLLHOQ5n1AvsRArcdk6facGYHPZ7Ogao5cd13Y_6KG_UxZcJLoNvoM_yW_TvY-qVqp2nN8ivbstdKIXVA47kKq4OACJT2E0qDOLOvTnKDaopT5CJ0S7NUBKhCB97NTYPhE9XasNyAGRBfJ7qiJmaLc1iKhvNXYX8_7RfJXg1AQS9vecH8CeRy9znsPY0s0d0niWzhsxcohX7Uz2ziM7u5SZizq3nqJaieRTdPBNnHAv0q63MkxtKJ0QpbCSX_u1qHiDxJ04JuflXEN1IeC2dJLTb9F-a9qktziKeIjvIP1a1fSbGsrBlgm0eIVBO2YTNsBdOMS4w4DYx2Gmke4mkVBw8eZ17Tsbj-aL9TD2klgBOJRQ4BfKSuwraipHtLC85KK-Y=w490-h209-no)

Run *sudo -u dd-agent dd-agent check RandomNum* to confirm that your new Agent check is running. 

Any custom checks will run every check interval, which defaults to 15 seconds unless otherwise specified.  

## Bonus Question Can you change the collection interval without modifying the Python check file you created?

You could change the default main check run loop to 45.

# Visualizing Data:

## Utilize the Datadog API to create a Timeboard that contains:
I have never worked with JSON files before, never written one. I decided to go with a different approach. 
I created the requested graphs using the graphical interface, and accessed its JSON file using the API. I relied on the following doc: https://docs.datadoghq.com/api/?lang=python#timeboards

## Your custom metric scoped over your host.
![](https://lh3.googleusercontent.com/YvRrZhv_YJbwji9wmwwkBC8wHyoLIwP-I1S1odotUe0j00GK5fhy4y3P0rQlyGHcAFxD0ttvATQgt-mBPbgusTFQFWrp58YO37-lKdwo-06MHK0XS1WcmojITwME575BinZjot4wj46_oNCM3LIldTp24ReaBmph84ZSRmIRxcTCZQhNDVGlH-2sEZsL50zLPA-rwiYKwC61CO5mDBp_RT-nbw6YMWSzEnUZdRdj7FLMgIfB35inVz4gD3hQ0u6HzcDWYf7ywGiUYDXSPu3VCWJHNM87c5HbEiG8E5HZlSP5_DN_Ms00A_CDSot8bWzvxkoBytYhcncwimHpFNajv844wMbhXHneNqnisd3DIIiVRDjqvjkLZXyMIhti02QvG1xoKTU2a65ytrv1ldgxXRDPsMgYiLDIoSoyQHBzhaA5-kt-ZjDyUXfyrmHMEylrl_CWekM5ZAvrKtU360bIwxbBrBpiycY06s5K6jrX9Rl6R6hQHqWxp1_ZUowsGCiOi-gx5CntxXxUJllmBEBM8jaqfslBb_wSO14NQ2hqgYyBOon5-6RxmO-PC9R157WPKTBXBhFp3k_yGLGzXkjGOKuVWAHcCGOVuCztl-KRWvk=w1050-h548-no)
## Any metric from the Integration on your Database with the anomaly function applied.
![](https://lh3.googleusercontent.com/gYOrIcRYPrLu1T23uqw41algMcNcOubvHd_bJSUS71e3Z63o9hC9Q8pI_Hfd9ZLpsDplKrTIC9L3syqp4ici0-0ApwPBBeC8CTv5r3sDDfHnTNp1nnggmcePdJG1QRtHRd-NINqBoEhtbDENbmUF5HFNSa94QYYFeAQqezI1k3zclVczXth0jVnz2gBoeYqoDinvBBSaf2cqjnI9-iQTipUZC6zvlj4NPYoE8fZFQ50wfKz20Rl4v-Bdo9q_aiySqQ6kbmJpxXd_RMIpHipzYrIo710wUcO3dzzKPz34nMOzFVM9AuLzbYqmk40OldFwkxHQL3_2UucVww_cLE9ZTkcW4wHNP8rHqI9qysF0vcySbvcfsNK5MjP9FVkH5FdTnSP_cDo32EBZI4oev9sDmU1CnLZm8OPzIkSmDCbhAZPzbBivY_Y_y4zL1nMY3eeT16YC0Vipu20-XPxMfzKjCB-KdjkMbBj3jqDo0Ay14b98p8yE-Cjj-pn3Nd5_DkZ0mHrienKyBHTDC8HIi73VCeFErW0H6cA8ruZJZ1U2m5ylQNs2ybcELbsGDyZRugNUVDMeusLRTRONRlpovAsUWHs25B1OT_75oXW8qwSDpHs=w1047-h548-no)
## Your custom metric with the rollup function applied to sum up all the points for the past hour into one bucket
![](https://lh3.googleusercontent.com/8vQwgg2DnJhyouRw2nE6ZIfHkYG0N2fzj0SPuosR7ti7SXszLCJU6gBp7IOdg31GNXZyI9GSg7drmlSQoyyyBP4wx7QtbCkSpPv6gu4ZVB7hIr5_jWYY7qF4z8KRxam8F0NDLaIrVP7jGq6nnYF59Dl2p65MZWkLM7ldEpe5FxsgAao1tfGYVSFavpI_xEbPSP3hwXAtLHpcTl6CDc_QiumdCBFZ96buwcTT0HJdbV8nyrNASVEn0_JQ003qhsvAXpv2PYFZdSvkWDkv50azwihKV3bhPT42nJuqq_PhKEVzmZ5hS8ARDMC7WBaWBHYg2tXneGCnmBFLu2ew0xR1VOhYSQskCQ3WhjqOzT5Qw1kruS1aYqbCjr07K8xsCkJHcNzpAdfpMMTA2v588bPqAHQNoivN4vg1vDTiU2d-kQ5PT33gd4OZlywNn_gT-ou_3UGGRSdRAFnzYm_GIesOixbPdT14p7Q7GF_1jJA_s25X8RaH5sTcpaQY9Fcgxnz9cNp0jmn7yGVtXJ5vEr9T6gIp7epR83bmF3gXSZ9VzJCTcoeDxWPdaTnb8SPeAlk2-BdtfQwO-t6p7y-11VfT48KWujI8ScX2qLb3kRDnAzU=w1043-h548-no)

You can find and examine your JSON file for the dashboard you created above:
Find you api and app key here: https://app.datadoghq.com/account/settings#api
Log in to the server.
Set your api_key and app_key variable.
To identify the ID of the dashboard run the following on your host: *curl "https://app.datadoghq.com/api/v1/dash?api_key=${api_key}&application_key=${app_key}"*

View the JSON file run the following on your host: *curl "https://app.datadoghq.com/api/v1/dash/${dash_id}?api_key=${api_key}&application_key=${app_key}"*

JSON:
```{
  "dash": {
    "read_only": false,
    "graphs": [
      {
        "definition": {
          "viz": "timeseries",
          "status": "done",
          "requests": [
            {
              "q": "anomalies(avg:mysql.performance.cpu_time{*}, 'basic', 2)",
              "aggregator": "avg",
              "conditional_formats": [
                
              ],
              "type": "line"
            }
          ],
          "autoscale": true
        },
        "title": "MySQL Performance- CPU"
      },
      {
        "definition": {
          "viz": "timeseries",
          "status": "done",
          "requests": [
            {
              "q": "anomalies(avg:my_metric{host:ubuntu.judit}, 'basic', 1)",
              "aggregator": "avg",
              "conditional_formats": [
                
              ],
              "type": "line",
              "style": {
                "palette": "dog_classic"
              }
            }
          ],
          "autoscale": true,
          "precision": "0"
        },
        "title": "my_metric -RandomNum"
      },
      {
        "definition": {
          "viz": "timeseries",
          "status": "done",
          "requests": [
            {
              "q": "avg:my_metric{*}.rollup(sum, 3600)",
              "aggregator": "avg",
              "conditional_formats": [
                
              ],
              "type": "line"
            }
          ],
          "autoscale": true
        },
        "title": "RandomNum- rollup(3600)"
      }
    ],
    "description": "created by szjudit@gmail.com",
    "title": "Timeboard1",
    "created": "2017-11-24T01:48:33.740609+00:00",
    "id": 406474,
    "created_by": {
      "disabled": false,
      "handle": "szjudit@gmail.com",
      "name": "Judit Szukacs",
      "is_admin": true,
      "role": null,
      "access_role": "adm",
      "verified": true,
      "email": "szjudit@gmail.com",
      "icon": "https:\/\/secure.gravatar.com\/avatar\/391633b31c0f7351ee8ffe5a293d1fdf?s=48&d=retro"
    },
    "modified": "2017-11-25T02:17:20.294136+00:00"
  },
  "url": "\/dash\/406474\/timeboard1",
  "resource": "\/api\/v1\/dash\/406474"
} 
```

# Once this is created, access the Dashboard from your Dashboard List in the UI:
## Set the Timeboard's timeframe to the past 5 minutes
The smallest interval I can set it is 1 hour. 

![](https://lh3.googleusercontent.com/9ktV_AIZPwdb25OPWwLG0GZ6IhIGdVD-Qkf9sVsiX-d3ThVmB8n9sw5oVg9gdVuPIPVdAy5s1Gzc5CKkd0m6iqeLpJmrojyz37KBu1392yftlBgXvcot4HoAOz9DAWIbOEQP5Nv-1ulGomm1u-sfJ8AH5b7L44-y8hv-Ze99PM4E_R6woaDpyrbJul5n5d-vpSQ88RV3pp83XT4jgYQm74vSAInyifrYC-L_5sep1_l4Aa6M7fGi2P-Q0D_ythEptI2CNvB8C9b39uO3cPlE69bPwyPpRzgT8EvIwYrWXyEU5e-09VpjQ6veOCTG3WlX2Ne9ki3XJ8vfU_5zLa9KXpxMMCB5nAGjKd4oAkgX5Rpw7gfIlC6AV0Sa2XV_SP3o0tRqliwPEOdvhbQfPbn1FGaPQ54STI1CNiJyiGbX5Qk9Oz-3TR1bH9f9JjU1jrKJPJWuWEFeUyEXFG9zu2-c2a-S2c4Sn6CGQ_4PZ1UtBDoZhjwR4blYmOnoat9bvAM4DtysXuAAeT3nEaIwPKaWCTRE7l2yh9ykVIExi4hpr6mHVAtDUpwTuNCiISNcb2VwaggANlYWTb8PhreXSpwoduy0X0RsKrwxCNGAolanFrI=w1193-h525-no)

You can however highlight any given portion of the graph to zoom in on the data. You can select 5minutes interval and take a screenshot of it by using the small camera icon from the top right hand corner. 

![](https://lh3.googleusercontent.com/QKduUhxUWhGao9Xwp7bT-U4erchZtuzRJhd_kxjwfypUKAYQ1Jfq2_lWkdLfsJfSlJuiMVI-vh3FP58vwWsJ1BE6um-eHBvJsKQbAS-SpxTtIz0Kom-FBsy8PxNN_maI4Ghu6X-skND_w9UKoTPre-MxNG1m7Hfg7QCr0vyuM3bVxcwUHP-eSyyQ79enr8-0MuW23Lnj7YwlNK4k8dmbKWciuM7ze8dyJKkP13hPAENLlvHXaw7SMTkaC0L-HWKgi-5AsUoDQEGtBad66FQ0K7lsBPmvLfx0jhLXsXh-u9UrwrKWgwQTrOeBfQaBUANrVp3MxfTcvUxJMl9Y8gpQ1GIaTifL5e8HOZBESwlsg3QzTOig7i4-c76ajvZhFTk0ixWr9UFDAuF2dqzK8D3MViA8_evCqS2cO9VMfJnEBudcVfHkaKbeKsg-ic6ULRUFPYDf8YxwxtpGNkQ_LjJDOV44P01FNUzhmgzMtHU9FNtVqiZJ0zDJFE5v3-fURuKGWFz2dgygjlsns-_16NM7gQ77wXtUxYapXLkG0Sl4jfhna3CTMw5YS5jqT5KCt7JaLxl7OTObRHLRzCXlNi15iMCxj0sIhHn2cTfyTCnPW6U=w714-h397-no)

## Take a snapshot of this graph and use the @ notation to send it to yourself.

I could not send the snapshot to myself in an email. I commented on it, which created an event on my eventstream with the snapshot and my comment tagged me in. 

![](https://lh3.googleusercontent.com/pB9sG13UPMrauEos8ONPiAVZLFd4IzzJjdtjt2bdo9BzBZ3Fr60Fl5UiUibxj951W2FJ5XUiU0ihTCgfla2qBXg6AiRRzZgW9S674VOclkIt38agymYPCM1e71F2dB20MrnWScnRiUpQHh1gPBZsd4VMckpdrXF9HsfQcH_Mu6tUxlM0i2TFp4l7EQa6fdUSw3tYPfpKUMpbcQRjeiAkkpM9b2jRSspaQudHqPUm11i8NF_mjAAsHsAgI3FhKXUEDBwGWyUstS6G-2TgP_EGesCY7-TXYVWNMewS6cCICfaABvGN4VV26i78jWu2DXwcw4PRjzrWBrrXuHEwULqEIgNgdVOZMKJbyAYiPOzv2onlbl4y9DdIyS7duF6DzcuGatrCSBgBfwOohgLnR7p0J1UBdlhZZxz4cp9D9CQoop0lZWOKpFPnNUYtLFJGFdNirPTPHuBGoyQQ8mbWvaeV7CVX1Ps3f2FwcwnHa2xwK3fOit9YGKRqhm3eQIn5KkAPAX3Gz38vLsp09xjAWvAEsZU-h6GOy5JBKwn4vO9OfFvuWED1W93RYPs_vcc8awMdLltyiRgPaA-l5fy_c7WyH1OVx1uOIJp125gPA_zeXio=w867-h315-no)

## Bonus Question: What is the Anomaly graph displaying?

# Monitoring Data

## Create a new Metric Monitor that watches the average of your custom metric (my_metric) and will alert if it’s above the following values over the past 5 minutes: Warning threshold of 500. Alerting threshold of 800. And also ensure that it will notify you if there is No Data for this query over the past 10m.

I followed the guidelines https://docs.datadoghq.com/guides/monitors/

1. Open your Datadog user interface and use the left hand side menu to open the Monitors menu. Click on New Monitor.
2. Select Metric from the list on the left hand side. 
3. Make sure you have Threshold Alert selected on the top of your page.
4. In the next step you select what metric you want to base your monitor on. Just start typing the name of the metric in the box, or scroll through to find the one.  In my case I used my_metric.
5. Select the host you want to monitor this metric on. 
6. You can use tags in the optional exclude box to not monitor certain group of machines. 
7. In the next box you can decide if you want to monitor the metric’s average, maximum, minimum, or sum.  In my sample I used avg.
8. In the next section we can set the conditions we want to trigger the message. 
9. Select above from the dropdown and set the time limit to 5 minutes.
10. Set the thresholds as per the requirements. In my case I want to receive an Alert if the average is above 800, a Warning if the value is between 500 and 800.
11. Scroll further down and select **Notify** if data is missing for more than **10 minutes**.

![](https://lh3.googleusercontent.com/N7oqIUPVvBOQP0vF33h1wUtWmBRy8lhw-4VuLE0Yvux6u8L3Nrv9gdYLGJbApBOUsamPWZV8gxxZvEM23cWGafI5Ky0rsxQRgYAUjNwWJn470MCucH-rmIDCd4Aly_JU19IbUb6uob4NGiReLuc-GsD0iTYej93XYn3uvRUjGV4Ov2x3-0-xMHBg54njJwDOP9g2sYJQF8zZJkacj0LAifcigycCG_5oR5LS0bVMP50h_QwpTraxVVoCbZ7wytJqgeUmAQRcO6gkLynnPPZYiS9ScD_-xpfO_G_MpMQ7CPIO5-smwCDccG47CjMdCdBKPgEnIv9zJkmC_-4SHyLj-bRSd2bQEJDLB66lStqxDyin0a11GLn04-LYkBOQbMuI8IP9z-FOT4zOPPqR4OByfYySWWXFmKcU8bDKDwPwQFQj50eH8clUV--temjGmwPAZ-llwCcWPmqFbwlf_OztTdmq7vaqtaIqEbW3H8aduXbqaEkP-BqSze0wALCpH0uYKqQjUKcWaIxRm0UP4My7NHHcabCvJCocESUZ5qcGN5ceimdjVJpwEYwcVhg2lKWFZ4NcXgI0XGqPEasrkzbVato_6D48CX-YOi0xe6ddKHc=w1026-h548-no)

## Send you an email whenever the monitor triggers. Create different messages based on whether the monitor is in an Alert, Warning, or No Data state. Include the metric value that caused the monitor to trigger and host ip when the Monitor triggers an Alert state.

In section four we can customize the message you receive for each event. 
1. First give a title to your monitor.
2. Type in {{ to see all available variable options or refer to our guide here: https://docs.datadoghq.com/monitoring/#message-template-variables
3. Check out my very basic sample case which sends you a different message for each scenario we defined in the steps above: Alert, Warning, NoData
```
{{#is_alert}}
## the sum of RandomNum average is over 800 in the last 5 minutes
value: {{value}}
Host:{{host.name}} on {{host.ip}}
{{/is_alert}} 

{{#is_warning}}
the sum of RandomNum average is over 500 but below 800 in the last 5 minutes
{{/is_warning}} 

{{#is_no_data}}
no data in last 10 minutes
{{/is_no_data}}
```
5. Type in the name of the person you want to be notified. 

![](https://lh3.googleusercontent.com/sSrHr411T2bKUokHJKgyj__9LL3kg7__KPbPr3MO9X3L_hd8jyZ-Bq5xFM3WJ5oP-lGsbYTrzGtTlwPUA1FtVqK9b7r-a5uHukIqDCHm-EitLwNixBV6_fc9ck51QzSFij3oqwN4UyH-ozXGoIXRp-MUfo5cZ6DdEOA29vPs0XLeL_rIaZNll4-Jp1x1-eGB_nS5zcjdkQWIcP5RHqpjBlR7Z_6zK83Iz1kgv7s7fHtKOJiycI3SMurPo41DjiXkhvHjTNK0wEKnb53DMzCcXXUfwX00XqJN4F3dyGyP6i0QdDUqX8gZcUWMt3Fy1UCUKo7Fz-P53gKUxHiUIf-FTiSPCQ3dftQP15NiXhFKtYcZXWct68mSUinPGn9wLGUMyIYE8fA_bPSULSUQaXwmeMeLItQEmLhk1AWKubxZMBN1pbXnUZ-t3zbGNjPzB3YvprxcQmA7XvMm8cTjZRvfqzMSvdBasNpb1f3Rl6INi3S0bvP-TkhIJfjroWwj1RLHNKgmQycbM5V7p9lrpiI6Gp6cVZnN1--2rSnSiKrxontWtV07FlHBnjKNXGhbtLFRFkdMAsukeWk9AdbXUSlpIYBnSuqkQ9wMveiBjoaESaA=w1002-h548-no)

## When this monitor sends you an email notification, take a screenshot of the email that it sends you.
![](https://lh3.googleusercontent.com/4jNy3AVMnAYT40niq2KDescsPnaaWzO779WhTHbhI3LtNuIfRKN1MC4HtfUm1pRB9f8RFaGVOhahIUKSg_FGNXeLueQR8xbXcZoeXhOnQmKiWdtNEnjky4svpWST4kBYhR61NQyMST33hyKv4qshKqf9GnsyBbDu79gSJmw1X5rADjhnTAzsbk-mThX6Cld8vbIo8lqjdZAEac-A8Ur0rNfmaiKJnZVOY4musPLDuWh9WNcz8bXDjH4DVidVL_q3aCf_0mztKiL3n0HjVahokRy75WKXyIgMnU1DlU2xf5MgNwdOi3ZxhMDw_kQssfci0-uvgB1KC_4O-ThpQvcZLvLZfVoq_PisaMJD9ARJsggixay8BguT0U8kMKRBmuION3sSNZomg4KtqpcwVtIf-tmWk21vgTDCRaGrgA_G94173ct0-n02zRzStynk-S-yrmgHUYdPsBcRtL2sJzLnCmVS1yGVqq1Gka-dabVJFLYkcoITjY7aSbj8yUm3eWviNDcJOiKNH3weHAXXNysSFmhy_mspf71PQWhe5tzbOihYSdfGdjCmg97_gwxLh8z7N8o0myR3Z9w97CKZIzxQ9pscYvEsJGiCX7qKLT4UWrI=w712-h511-no)

## Bonus Question: Since this monitor is going to alert pretty often, you don’t want to be alerted when you are out of the office. Set up two scheduled downtimes for this monitor: One that silences it from 7pm to 9am daily on M-F, and one that silences it all day on Sat-Sun. Make sure that your email is notified when you schedule the downtime and take a screenshot of that notification.

Downtime set to Monday-Friday, 7pm-9am:
![](https://lh3.googleusercontent.com/ekudlH0rXyggmNmJi98DWQoVZSD39miKqiw03L3hAI-9yt7Ct2oZW6DJiHGBY7OpSCkib8DN4o9l1hi2L5CZkobUqp73Lidp1tVQ3oQVjwbuzKjgijt7IEqNCTQvRiw_nhU-SO3uNYjPguxNF-3lZU3yqoxT540XU0Qyl5OZiuX4syCN0_jAhQEfPsAKnnkygdRZ5fLYjIbAaAHeH46rj4h-c-hbFpLz8ZSPeNRS5MR8lU3ahg5GJrDeSQyB1XpGS4CyA3GTeQBOSr_A1mSp4P0GD5jMtqOhYmJNpxU4A7NUu_Pq_t-Yi_tqovYdSdxIrMSIxS5PBFxTND2VSBFdP8Pyq4IGJLAta4dEd-OUMl-hgBxd3QXhZiuOy0v_huP668Y4E4SJd-D2YrgTm9iqUpWfHh3BidpFEn-sRgOh5wnGmOafk7ir--q-cELq12IDkM68X4KOEcf_4zvX22La8TbwxJSilB03V6_kwaXBd1cjgeWEUH_X3o-HJqtmOzZVFYuaXzUn7__AdRgGMYv2ogCyaoXwkf7J-3X1W7qA9hm-5Rw_F6YxeN3-jV8nyOc41c0rjYzPtEE06QK7j-8Uq8NJ4JeXlY-AUVVB_xwLBvU=w684-h548-no)

Downtime set to Saturday 9am to Monday 9am: 
![](https://lh3.googleusercontent.com/OlasytV0pU6UV8woA2_mfYWlPMi6jOgLHzEK73CZLqi5KiK5kQ6Jgn1uijmjMlIS-Wxnm-3nT9UoJP-4udbOdM8iPjfDspcH-1e979Lcl9fO6dbmOtaEfV1Y25KQwHetsLEidLRB0ZoJUDkRYEEDihLWsnvrt7dGlBNdETmZtdVjmlIcF4fhfvOCGBd0ftVmGsUFjAIVcB66OZDC891uhPnGmw5Sbs6gmLWnkFZ0_vqnfY1H7_qB1ymkLfOg9tRbITP75UtcMkMmNzS3IvJY2cjvvY82Z-WEOmqWYWxAEX2KfO96Uditb1-sDxbj6bk_SEJQcdS2N71tRgjyBRY5wSy1ahri8Xq1UoYlxm-PysA4U4TvOwUKQDdK9lTATOMVTxegX5j-4h4xz8nYJYKfCiuoyHvZu55oMqKc4hRx8ifEwQ-gDKM5NEEU4t-QpAxUO4szxRHiPIKEgCA1OJ3E8j7BJEGazbMGeOxgMV10KByR7-Qh1hZcPIDGDEOI6MMIp7EdgBQdcooSNuYghDklBA49Ccc4g6jINkZXqZtYHzCfljZgc1w0Eo5yGmqwqk4kuGB8SnO3IZPtUELFSp_kTkYFoD1vGZS3kQn3AKM7frI=w719-h548-no)

Email received:
![](https://lh3.googleusercontent.com/Iex3fHF9g-Qb_XF8ZVW6h2Z6tE3twsf1mwEUFwqxTkKa43fpckuKq_IEQcWZdAGOPC6Z2fhf2CAaJ3Fs07KUd_4OPBAqGf-YtBVgPz15fvZ7BnBLudwdfLe9v1VbO4EZRqmytoTmPck8DutXG3e32bxB48CZNFQ435loOjP9WT4Rnpik6XE_Vq2RRuj2bjqpjQPQVXmYQL8pY1IWZR5xYcQpb-VbRQlZLLUHoo_j6Rxbpv77k8f10MFGhsW4kmrNDgVQC6EuDUEMt9ykRMd1h_xcOsZiTll1Qb1ShKDrSzT9doj6XAcSzYBsTh6W2SPXvfckV-tzihENBHubSVfeEzWWid-CzjZzGi1L1buewpLjtDj9Dfmq2SBugOc1y0itzOcLtYc1ysATsPiFYgxzWJUwhPus0WW_3HsHNPbm8TcmJ-np2R8I3HCyGCx-7i-LsyPp6VtDaEo4tk-QpTnZG6uqLWWAPNNHoG-xb1PlvqEbxNvWKvnS9cgLsO3Uto0mCSdqwh1PBOW96DWa4Scm5tgOJ3ElH37xfQxGkKYG2lnrCtLv-ZOQj8urOaO5qIBNeBJTUbylGouV13gpTBLg6LxHYEXjUDeQy_Rhlz3A3yE=w901-h461-no)

# Collecting APM Data:

## Given the following Flask app (or any Python/Ruby/Go app of your choice) instrument this using Datadog’s APM solution.

Datadog’s APM allows you to collect performance metrics by tracing your code to determine which parts of your application are slow or inefficient.
To demonstrate the usage and available metrics let’s create an application and monitor its performance using ddtrace agent. For more detailed guide click here: https://docs.datadoghq.com/tracing/

1. Copy and paste the code into a python file on your host: *sudo nano Flask.py*
2. Run the Trace Agent for your Flask app: *sudo ddtrace-run python Flask.py*
3. To see the data captured by the Trace Agent navigate to APM on your UI’s menubar and select Services. Click on the name of the service to see a detailed view. It might take up to 5 minutes for data to show on your Datadog user interface. 
4. You can trigger more entries by opening a new shell and running: *wget -O - -q http://127.0.0.1:5000/*
5. You can use the collected metrics on any new or existing dashboards.  When adding a new graph **type datadog.trace_agent** in the **Get** field to see available metrics. 

![](https://lh3.googleusercontent.com/lnPF_WWXKa1MPWwzfGsrw0iAcJmYFJSuU4ZGE2eSJL4Pk2Otp4U-CKHU9IJWgKs7K3gtsvtUqL1qll1XiTLEa0V_bbx7qUlKZOUb86v8CtEGYYYAHJEhjgR6sqx88qAakKIFykN0KrEJPjGZRlmM78CMp71noUFYgf1l_T8-Za4ak63I5ezN-L1NF5VAtXDJtXzLz7RbxYZrmk64fwlrXP-pNWtEcPfpnrTfzLlnE0bD6L24gLFhpCQGFKRHrDU-M3nB6hchEA1IsRIuMQI8PuuoquvmSXz4ULlfRC-Nq27cLvcZ_11x57yKoxYTotJUXWMYqfYUSXxxn9BJI0X8CETxtu6WvVE4KN3eZ8rW2jSJlXj1Xx_jGU-TuzXQ94pZkycqeLgNirCGJMFzUbBpd608CiwiIu06funZPjgXQxDSg0vdX3OZpRl0ShnBtYErujFdI2_IT13gcgKOsOUHE-joJZSzFIJYIBM0nzl0n2cRmh8O45uLi9qY5Hrm7q6YfBJjaemc64AuuouqVFIYWkyGKBuBxzZqj__kh8xh77s-MJzAKXvwRo515g5JXiyshGryNlpcHJ8SCmLJFr_mk3_jUKKEsPJDBglDT8ZWNEU=w1017-h548-no)

## Bonus Question: What is the difference between a Service and a Resource?
Service is the name of a set of processes that do the same job. Resource is particular query to a service.
You can find more information on Tracing Terminology here https://docs.datadoghq.com/tracing/terminology/

## Provide a link and a screenshot of a Dashboard with both APM and Infrastructure Metrics.
https://app.datadoghq.com/dash/407067/screenboard1?live=true&page=0&is_auto=false&from_ts=1511644260000&to_ts=1511647860000

![](https://lh3.googleusercontent.com/nzRXYKZvAYsjFS0l48U7Bq4t7EoiEeNh19SpAprgkg5xXatYDOPDk5SK0NJxfcPXxfE6uDjKpNn_SqnBh0FqQiYtOez-ZtsKXejc6g1yTvtl_KxKrhwTSuCxnHK9nwY9IM3ns2mAtAy2kc_R8dbx6kyjqTJN92UUexQxgnPJzIrFly7Lr3zIHsJVWqS2r-IR7ilfHtSAJhXT7aAetAqhr-Cmaqjk2-EEckoy8g-wGvP2tRgPrHL_qymwPawRouLp27C3Q6sS_-TqesmHHvolDwKMO2BDvkd9hnVxZhZJ1lFtV03brnOig8EyvxI5PPfQ5tMN42yxG7WPADrhQjseRjTpc5FZ35pMOaL2UADbCgovUxz8ji2ULt1yqM33gVyTJf0aFMs3ID2_P2Gps-pAhErIkUGGOZrOm_17gApI6rmsuyO1BbPcqSZrNdV58XNlszdaW-1MeQ43NTLI-DgQOoSIdmsNP9o3yl2Rv3fYNogE9E8m4KDQLTH1QI-u2Eq8jqoC0-16TozO_W4RqWE4UcMMPU64BlbCgxz6JVMSQDgQ7lCY8W4pA1djpfljlIT6WrNnWQ0JEDjOufja4mFdpDHBB4OwkcC6DwPkorb5HbE=w1070-h548-no)

# Final Question

## Datadog has been used in a lot of creative ways in the past. We’ve written some blog posts about using Datadog to monitor the NYC Subway System, Pokemon Go, and even office restroom availability! Is there anything creative you would use Datadog for?

