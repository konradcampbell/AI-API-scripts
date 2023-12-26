#projects 

Click this link to view the [[CoverletterGPT Explaination]]

from openai import OpenAI

client = OpenAI(
    api_key="API-KEY"
)


def generate_cover_letter(context):
    """
    Generates JSON Cover Letter based on context provided from API.

    Args:
        context (str:json): A JSON context object provided applicant/job information.

    Returns:
        JSON: A cover letter object with filled in details.
    """

    generate_chat_completion = client.chat.completions.create(
        model="gpt-4-1106-preview",
        messages=[
            {
                "role": "system",
                "content": "You are CareerGPT and your role is to semantically create an exceptionally articulate cover letter using the context provided. You must strictly generate the body of the cover letter, which means you must not include the header, contact section, or footer. You are given a job description, hiring manager, employer, applicant information, and applicant background. Do NOT assume anything about the applicant unless it’s specifically given. With this information, semantically parse the context and utilize it in the letter as seen fit. You must OUTPUT in JSON, there are no exceptions. Make it no longer than 265 words while keeping it creative. Do NOT put any quotations such as double quotes or single quotes in your response other than part of the json object. Do not include it in the content of any element within the json object as it must be a valid RFC. Do not include any n or n characters in your response. Do NOT include a Sign off such as Sincerely or Best Regards."
            },
            {
                "role": "user",
                "content": """
                I am providing you the letter context below the dashes, this includes my details, the employer, the hiring manager, the position, the job description, and my background. Utilize these to make me a great cover letter body with the sections I told you to provide me. Below the two dashes is the context. If anything isn't specified, make it generic. An example of this would be, if a hiring manager isn't specified, then say "To Whom It May Concern" or of some variation. Do NOT put any quotations such as " or ' in your response other than part of the json object. Do not include it in the content of any element within the json object as it must be a valid RFC. Do not include any \\n or \n characters in your response. Do NOT include a Sign off such as Sincerely or Best Regards. Please emphasize my skills and make the cover letter large enough to cover a full printer paper. I want the JSON you provide me back to be in exactly the following format:
 
            {
                "cover_letter_content": {
                    "addressment_and_greeting": "",
                    "introduction_and_application_reasoning": "",
                    "past_experience_and_skills": "",
                    "position_alignment": "",
                    "closing": ""
                }
            }
 
            -----------
            Here is the context:
            """+context
            }
        ],
        response_format={"type": "json_object"}
    )
    return str(generate_chat_completion.choices[0].message.content)

generate_cover_letter(str({
  "id": 7112107016356798465,
  "user_id": 7615,
  "template_id": "cv-visionary",
  "template_theme_color": "#c8c123",
  "cover_letter_context": {
    "job_title": "RPA Developer",
    "job_description": "Role and Responsibilities: • Develop on-premises, and attended RPA bots for processes identified by NTESS. • Coordinate, conduct, and document simulation and testing of proposed bots in accordance with direction from the SDR. Testing will require successful use case, performance, acceptance, and user experience (UX) testing • Resolve issues identified in testing within a timeframe provided by, and to the satisfaction of, the NTESS SDR • Identify changes to processes impacted by bot implementation and develop new process documentation in a format(s) designated by the SDR and in collaboration with staff • Work with business areas to establish expected service levels for bots prior to production deployment • Generate performance measurements for the bots based on required objectives • Promote bots to the production environment in accordance with direction from the SDR and IT • Validate that both are working as expected in the production environment to the satisfaction of the SDR. • Collaborate with staff to develop/implement training materials for staff to use and maintain the bots. • Provide troubleshooting and issue support to bot users as issues are encountered. • Create and provide documentation on the design and configuration of each bot in a format designated by the SDR and IT to allow for post-implementation maintenance of the bots • Resolve issues identified in documentation within a timeframe provided by, and to the satisfaction of, the NTESS SDR Required Education and Experience: • At least Bachelor of Science degree (Masters Preferred) • UiPath Certification • Five years of Bot Developer Experience • Excellent verbal and written communication skills. • Previous IT experience with the Federal government is preferred.",
    "employer_information": {
      "employer_name": "Leidos",
      "employer_industry": "Professional Services",
      "hiring_manager_name": "Leidos"
    }
  },
  "cover_letter_content": "None",
  "save_applicant_info": True,
  "applicant_information": {
    "applicant_name": "John Smith",
    "applicant_email": "johnsmith@example.com",
    "applicant_phone": "+1 (123) 456-7890",
    "applicant_address": {
      "applicant_street_address": "123 Fairytale Lane",
      "applicant_city": "Sterling",
      "applicant_state": "Virginia",
      "applicant_zip": "20176",
      "applicant_country": "United States"
    },
    "applicant_clearance": "Secret",
    "applicant_current_title": "Cyber Security Engineer",
    "applicant_current_organization": "Leidos",
    "applicant_highest_education": {
      "applicant_diploma_type": "Bachelor's Degree",
      "applicant_field_of_study": "Computer Science"
    },
    "applicant_background": {
      "applicant_experience_years": "6",
      "applicant_seniority_level": "Mid",
      "applicant_work_exp": "None",
      "applicant_certifications": [
        "Certified Entry Networking Technician (CCNA)",
        "Splunk Enterprise Certified Architect",
        "CompTIA Network+",
        "CompTIA Pentest+",
        "CompTIA Security+",
        "Certified Ethical Hacker (CEH)",
        "Certified Cloud Security Engineer (CCSE)"
      ]
    },
    "applicant_skills": [
      "IDS/IPS",
      "TCP/IP",
      "Splunk Enterprise",
      "Nessus",
      "NMAP",
      "Metasploit",
      "Kali Linux"
    ]
  },
  "created_at": 1695658449,
  "updated_at": 1695658449
    }))