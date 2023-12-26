To view the [[Website VisionGPT Explaination]] click the link.

from openai import OpenAI

client = OpenAI(
    api_key="API-KEY"
)

	# gpt-4-vision-preview
	# type - image_url
	# image_url { url }

def generate_sketch_code(sketch_url):
    vision_completion = client.chat.completions.create(
        model="gpt-4-vision-preview",
        max_tokens=4096,
        messages=[
            {
                "role": "system",
                "content": "You will be taking a wireframe I provide as a sketch and converting it into a fully designed website. We will require you to generate html/css/js for the full site and return only the code."
            },
            {
                "role": "user",
                "content": [
                    {
                        "type": "text",
                        "text": """
                       
                        Hello GPT4! I am building my company website. We are an AI solutions company. On my website I want it to be a catalog of solutions we have made and models the public can try out. I have sketched out a wireframe to use when designing the base html of the site. Please match the column and flex structure as outlined in the provided image (3 columns/boxes per line)
 
                        Please ensure the solutions and models are 2 separate sections, one above, and one below.
                         
                        The company color is: RGB(53,99,128) - make sure to use this on the page for the styling - feel free to tune this for the accent colors.
                         
                        Below you will need to insert the respective urls for where they go.
                         
                        LOGO: https://244cba.p3cdn1.secureserver.net/wp-content/uploads/2020/03/GovAcq_Logo_clear.gif?time=1698986763",
                        SOLUTION_IMG1: https://244cba.p3cdn1.secureserver.net/wp-content/uploads/brizy/imgs/capital-cap-702x526x3x0x695x526x1589519782.jpg
                        SOLUTION_IMG2: https://244cba.p3cdn1.secureserver.net/wp-content/uploads/brizy/imgs/VideoCAP-725x543x0x0x725x543x1589150374.jpg
                        SOLUTION_IMG3: https://244cba.p3cdn1.secureserver.net/wp-content/uploads/brizy/imgs/TacticalCAP-725x542x0x0x725x542x1589150372.jpg
                         
                        For the models, use feather icon - fully implement this and pick the best icon for the model. Do not put in placeholders.
                         
                        Make sure each of the solution/model cards are styled with borders, accent colors, and box shadows.
                         
                        Make sure the logo is small enough to be in the navbar, and ensure all navbar elements are visible.
                         
                        Make sure the copyright has the company name: Government Acquistions Inc. (GAI)
                         
                        Return me back pure HTML, inline css, and javascript for the final version of this site.
                                                
                        
                        """
                    },
                    {
                        "type": "image_url",
                        "image_url": {
                            "url": "https://cdn.discordapp.com/attachments/870877265506992240/1180343900167213187/IMG_7046.jpg"
                        }
                    }
                ]
            }
        ]
    )
    return str(vision_completion.choices[0].message.content).replace("\n", "")


	# Single pass
print(generate_sketch_code("https://cdn.discordapp.com/attachments/870877265506992240/1180343900167213187/IMG_7046.jpg"))

	# Generate multiple outputs using a for loop
for _ in range(5):  # Adjust the range as needed
    result = generate_sketch_code("https://cdn.discordapp.com/attachments/870877265506992240/1180343900167213187/IMG_7046.jpg")
    print(result)
    print("\n" + "="*80 + "\n")  # Separator for better readability