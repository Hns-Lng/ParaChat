# ParaChat
## Building a specialized chatbot using retrieval augmented generation.

#### Status Quo:
Skydivers have to keep their equipment airworthy to jump, this is done by repacking the reserve canopy every 6 or 12 months, depending on the country. the reserve and the container/harness system usually get an annual check-up at the same time. 
This has to be done by certified personell, as the reserve is the very last resort in case something goes wrong before.

riggers are being trained on most brands and products, and most of them are built roughly the same, they only differ in small technical and optical details. In order to do the work to the manufacturers specifications riggers take the owner's manual and look up details they are not sure about.

## Problem:
when working on multiple different systems everyday it is annoying to go through the whole manual to look for that one detail.

## Solution:
centralized knowledge base with all manufacturer's manuals loaded to. A Large-language-model (in this case GPT-4o through OpenAIs API) powering the natural language in-  and output.

The streamlit web UI runs using the streamlit plugin of Lightning.ai, so if the `V4.ipynb` script is opened in a Lightning.ai studio you can simply run it from there.

The different manuals were placed in a separate folder, that's all we need.

We load, split and embedd each manual in a separate vectorstore once in the beginning, this does not need to be repeated unless we change something in the manuals.

___

picking a container system from the dropdown triggers the loading of the corresponding vectorstore so it is available for the retriever.

we add memory and a simple prompt template, explaining to the LLM what it's job is.

The last step is to chain LLM model, retriever, memory, prompt and the output of retrieved context together, so it can be used by the streamlit related code to process the query.
