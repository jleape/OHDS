# Open Hardware Design Specification

The Open Hardware Design Specification (OHDS) is a standardized format to document designs so that makers and apps can easily interpret them.

The specification is designed according to the following principles:

* stability - early feeds should not have to be updated to remain valid
* flexibility - the feed should accomodate any conceivable type of hardware
* minimalism - producing a valid feed should be as simple as possible
* open - all of the files should be in open-source, widely compatible formats
* readability - the data should be readable to both humans and machines
* JSONifyable - the text files should be directly translatable to a JSON object, so fields may contain arrays of values

Any request to modify the OHDS must demonstrate how it satisfies each criterion.

All .txt files must be tab-delimited tables. The order of the fields does not matter but is most readable as presented here.

---

## Required Files

An OHDS feed must have the following files in order to be deemed valid.

### feed_info.txt

Basic information about the ODHS feed.

* first_post (dd-mm-yyyy) - 17-01-2019
* last_updated (dd-mm-yyyy) - 17-01-2019
* language (ISO) - en
* contact (email) - jleape@gmail.com

### product.txt

Basic information about the product.

* product_id (string) - vip_outhouse
* name (string) - VIP outhouse
* type (string) - building FIX: look for relevant ISO code
* description (string) - a standard outhouse ideal for areas with no plumbing and a hot climate
* features (string) - heat-induced ventilation, odor seal layer, 2000 uses
* ohds_repo (string) - https://www.github.com/jleape/VIP_outhouse
* open_source (boolean) - 1 [0]
* skills (string) - concrete pouring [arc welding, soldering, sewing, etc.]

**Optional**

* copyleft (boolean) - 1 [0]
* logo_attribution (boolean) - 0 [1]
* disclaimer (string) - The designer accepts no liability for damages caused by the production, use or disposal of this product.

* currency (ISO) - USD
* royalty (real) - .15 [fraction of sale price]
* subscription_price (real) - 25
* subscription_time (real) - 1
* time_unit (string) - month [day, week, year]

* parametric (boolean) - 1 [0]
* min_scale (real) - 0.3 [fraction of original size]
* max_scale (real) - 2.5 [fraction of original size]

* video_repo (string) - https://www.youtube.com/user=39014ie2/playlist=w49023
* code_repo (string) - https://www.github.com/jleape/VIP_outhouse/code

### designers.txt

Basic information about the designer.

* designer_id (string) - jleape
* name (string) - Jonathan Hoagland Leape
* designer_repo (string) - https://www.github.com/jleape

**Optional**

* lat (real) - -37.5902
* lon (real) - -73.8315
* role (string) - designer, engineer
* components (string) - 4 [component_id]

### equipment.txt

Equipment necessary to create the product, including protective gear.

* equipment (string) - concrete mixer
* quantity (integer) - 1

**Optional**

* sku (string) - 4930S29F
* sku_alt (string) - 38F4832I04, 28S4038E58, 18Z5386N60
* requirements (string) - rotating drum, capacity greater than 100 kg, capacity less than 500 kg

### materials.txt

Materials required to make the product.

* material_id (string) - 1
* name (string) - cement
* quantity (real) - 50
* units (string) - kg [any metric, any imperial]

**Optional**

* sku (string) - 5A83U902
* sku_alt (string) - 18F43321C4, 19538S6X0, 28D8032E58
* url (string) - https://www.alibaba.com/construction/18F43321C4
* url_alt (string) - https://www.homedepot.com/construction/18F43321C4, https://www.builderswarehouse.com/construction/18F43321C4
* description (string) - quick-drying, extra-strength

### instructions.txt

How to make the product.

* step (integer) - 2
* instruction (string) - mix cement, aggregate and water
* duration (real) - 25
* time_units (string) - minutes [seconds, hours, days]
* materials (string) - 1, 3, 4 [material_id]
* equipment (string) - 1, 5 [equipment_id]
* iterations (integer) - 1

**Optional**

* component_id (string) - 5
* components (string) - 2, 3 [component_id]
* drawings (string) - 5a, 5b [drawing_id]
* tutorials (string) - https://www.instructables.com/tutorials/concrete-mixing, https://www.builderworld.com/tutorials/concrete
* video_id (string) - 4
* video_moment (string) - 0:1:43
* photo_id (string) - 9

### photos.zip

A compressed folder of images of the final product. All photos must have a white, shadowless background. The folder must include one axonometric photo of the final product named 'axon'. 

The folder may also contain any number of detail images named with a unique photo_id referenced in instructions.txt, components.txt and photos.txt. 

All photos must be saved in any of the following formats:

* PNG
* JPG

**Optional**

Photos meant to render a 3D model of the product should be placed in a subfolder called "3d".

A logo may be included, and must be named 'logo'.

___

## Optional Files

### components.txt

Assemblies of materials that may be duplicated in a product or used in other products.

If a component has its own OHDS, its component_id here should equal the product_id in its OHDS feed.

* component_id (string) - 5
* name (string) - crescent door

**Optional**

* materials (string) - 3, 5, 6
* description (string) - a durable wood door with a crescent window
* ohds_repo (string) - https://www.github.com/aschweinbacher/crescent_door

**Optional**

* photo_id (string) - 4a 

### drawings.txt

A description of included drawings

* drawing_id (string) - 2a
* perspective (string) - top [axon, explosion, front, left, right, back, bottom]
* description (string) - plan view of the concrete foundation

**Optional**

* component_id (string) - 3
* tolerance (real) - .05 [fraction of dimension]

### drawings.zip

A compressed folder of design drawings. 

Each drawing must be saved as a separate file and named with the id referenced in the drawings field of instructions.txt. 

Any products requiring the use of CNC machines must include exact CAD files, which may be submitted without dimensions in one of the following open formats:

* SVG
* DXF

Inexact drawings must be fully dimensioned and submitted in any of the following formats:

* PNG
* JPG
* PDF
* SVG
* DXF

**Optional**

* tolerances for each dimension
* color_id labels on areas
* a scale, although it cannot replace dimensions

### attribution.txt

References to other designers and products that somehow influenced this design.

* attribution (string) - inspired by [copied from, modified from]

**Optional**

* component_id (string) - 2
* designer_name (string) - Albert Schweinbacher
* designer_id (string) - aschweinbacher
* source_product_id (string) - crescent_vip
* odhs_repo (string) - https://www.github.com/aschweinbacher/crescent_vip
* source_component_id (string) - 3

### transcripts.txt

Transcripts of the videos in case automatic captioning is inaccurate.

* video_id (string) - 4
* transcript (string) - Set up the concrete mixer in a well-ventilated area. Test that it runs properly, and then add the cement and aggregate...

**Optional**

* language (ISO) - en
* video_moment (string) - 0:1:43

### photos.txt

Metadata for the photos.

* photo_id (string) - 3a
* perspective (string) - top [axon, explosion, front, left, right, back, bottom]
* description (string) - top view of the outhouse with the cold color scheme

**Optional**

* swatch_id (string) - pastel
* maker_id (string) - yumi_builder

### swatches.txt

A set of swatches recommended by the designer.

* swatch_id (string) - pastel [warm, cold, primary, secondary, color-blind-safe, christmas, halloween, etc.]
* color_id (string) - trim [main, button, interior, etc.]

Must include one of the following fields:

* hex (string) - #FFFFFF
* rgb (string) - 124, 53, 97
* cymb (string) - 42, 75, 145, 16

**Optional**

* color_brewer_id - 4308S49 [swatch id from colorbrewer]