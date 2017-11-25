My understanding of the exercise is to provide a step by step documentation for a potential Datadog customer or client to follow. I don’t know the client base of Datadog and so I cannot guess the technical skills of an average client. I am also not an experienced system administrator myself and I don’t necessarily comprehend the significance of each function I used in Datadog. I don’t know the terminology used and prefered by Datadog.  As such I don’t think I can provide a documentation that would serve the best interest of any potential Datadog client.  

# Prerequisites - Setup the environment 
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
We offer several ready to use integrations. You can find the full list of available integrations form your Datadog website (https://app.datadoghq.com). You can find the available metrics for each service by clicking on the name of the service and choosing the Metric tab.

1. After logging on to the UI, use the left hand side menu bar to navigate to Integrations and click on Integrations. 
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
