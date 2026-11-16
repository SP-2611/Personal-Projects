# Credishion

**Explore the cultural stories behind clothing.**

Credishion is a planned computer vision web app that will let users photograph or upload a garment, explore its possible cultural connections, and discover relevant sellers in the regions associated with those traditions.

> **Project status:** Planning and early development. The MVP blueprint is complete; the application, recognition model integration, and seller catalog have not yet been implemented. There is no working demo or installation package yet.

## Why this project?

Clothing is often shared, adapted, and marketed across borders. A product listing may say little about the traditions, communities, or craftsmanship connected to its design.

Credishion aims to make that context easier to explore and help users discover makers and sellers connected to those traditions. This is a beginner personal project for learning Python, computer vision, and web development.

## Planned experience

1. **Capture or upload:** Take a photo or choose an existing clothing image.
2. **Explore possible matches:** See garment categories that visually resemble the item.
3. **Learn the context:** Read a short, researched heritage card with source links.
4. **Discover sellers:** Browse a curated list of sellers offering related garments.

The app will focus on possible cultural associations. A photograph cannot establish an item's exact origin, maker, material, or authenticity.

## MVP scope

The minimum viable product (MVP) is the smallest version that completes the photo-to-information-to-seller journey.

- [ ] Upload and preview one clothing image.
- [ ] Capture a camera snapshot, with upload as a fallback.
- [ ] Browse three researched garment categories manually.
- [ ] Suggest possible matches using a pretrained vision model.
- [ ] Show an uncertain or unsupported result when appropriate.
- [ ] Display sourced heritage information for each supported category.
- [ ] Link to two or three checked sellers per category.

Initial categories will be selected after reviewing available sources and permitted images. Worldwide coverage, live video, payments, and exact-product matching are outside the first version.

Here, **local sellers** means sellers in a region associated with the selected tradition, rather than sellers near the user's current location. Seller location, community connection, and shipping availability will be listed separately when verified.

## Planned technology

| Tool | Purpose |
| --- | --- |
| Python | Main application language |
| Streamlit | Web interface, upload, camera, and results |
| Pillow | Read and prepare images |
| CLIP through Hugging Face Transformers and PyTorch | Initial visual-matching experiment |
| JSON files | Small heritage catalog and seller directory |

CLIP is a pretrained model that can compare an image with text descriptions. Its usefulness for the selected garments must be evaluated; its ranking is not proof of cultural origin.

## How the parts will connect

The interface will receive a photo and pass it to the visual-matching component. That component will return candidate garment IDs. The app will use those IDs to retrieve reviewed heritage information and related seller entries.

For example, `garment_001` will identify the same category in the recognition output, heritage catalog, and seller directory. Historical descriptions and seller URLs will come from reviewed records, rather than being invented by the model.

## Proposed project structure

These files describe the intended implementation; they are not all present yet.

| Path | Responsibility |
| --- | --- |
| `README.md` | Project overview and development roadmap |
| `Credishion_MVP.md` | Detailed MVP blueprint |
| `app.py` | Interface and user flow |
| `matcher.py` | Model loading, candidate ranking, and uncertainty rules |
| `catalog.py` | Load and validate catalog records |
| `data/garments.json` | Garment names, cultural context, and sources |
| `data/vendors.json` | Seller details and relevant product links |
| `requirements.txt` | Dependencies and tested versions |
| `evaluation/` | Evaluation notes and permitted test-image references |
| `.gitignore` | Exclude private images, secrets, and environment files |

## Getting started as a beginner

**First goal: display an uploaded clothing photo on a webpage.**

Build the project in small milestones:

1. **Check Python:** Open PowerShell on Windows and run `python --version`. Record the version or error before setting up dependencies.
2. **Build the upload page:** Create `app.py` with an upload control and image preview.
3. **Add one heritage card:** Let the user manually select a garment and read reviewed information.
4. **Add a real seller link:** Connect that garment to a checked seller entry.
5. **Expand the catalog:** Research the other supported categories.
6. **Integrate recognition:** Add the pretrained model and map its outputs to catalog IDs.
7. **Evaluate and share:** Test mistakes, uncertain inputs, and phone usability before deployment.

Installation and launch instructions will be added once the application files exist and a working dependency setup has been tested.

## Cultural information and seller data

Each heritage entry should include the garment's name, alternative names, associated communities and regions, a short history, limitations, and supporting sources. Prioritize museums, cultural institutions, scholarly work, and accounts from makers or communities.

Each seller entry should include its name, location, relevant garment IDs, website or product link, business type, and date last checked. Record evidence for claims such as artisan-owned or community-connected; use “unknown” when unverified.

Seller suggestions will be labeled as related items. Location alone does not establish a seller's cultural connection, and a link does not guarantee current stock or shipping.

## Responsible recognition

- Present visual matches as possibilities, allowing shared or overlapping traditions.
- Keep cultural association separate from place of manufacture.
- Do not infer the wearer's ethnicity or religion.
- Do not judge cultural appropriation from a photograph.
- Do not present model similarity scores as authenticity percentages.
- Include an “I'm not sure” result and manual browsing.
- Use reference images with appropriate permission or licensing.

The planned privacy approach is to process uploaded photos without deliberately retaining them by default. The implementation must be checked before making this guarantee to users. A hosted app will send photos to its server for processing.

## Evaluation plan

Use separate development and held-out test images, keeping duplicate photos and photos of the same product together. Include unsupported clothing, lookalikes, blurry photos, and non-clothing inputs.

Track correct matches per category, whether the correct category appears in the top three suggestions, how often unsupported inputs are accepted, and how often the app returns “not sure.” Report sample sizes and limitations alongside results.

The MVP is ready for a small user trial when someone can complete the intended journey, every displayed heritage card has reviewed sources, seller links have been checked, and recognition limitations are clearly communicated.

## Learning resources

- [Streamlit documentation](https://docs.streamlit.io/)
- [Streamlit camera input](https://docs.streamlit.io/develop/api-reference/widgets/st.camera_input)
- [Streamlit file uploader](https://docs.streamlit.io/develop/api-reference/widgets/st.file_uploader)
- [Hugging Face zero-shot image classification guide](https://github.com/huggingface/transformers/blob/main/docs/source/en/tasks/zero_shot_image_classification.md)

## Future ideas

After validating the first version: expand garment coverage, add textile and motif research, improve matching with permitted reference images, gather community feedback, and provide shipping filters for sellers.
