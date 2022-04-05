Column Definitions
==================

Equipment types
---------------
Accessed with :code:`pd.json_normalize(client.get_equipment_types())`

**id**: unique integer associated with the given type/tag

**tag_name**: short name generally used in scripts

**name_long**: longer, human-readable name (e.g. tag "cogen" => "Cogeneration Plant")

**name_abbr**: common abbreviated form (e.g. "FCU", "CHWS")

**active**: ???

**flow_order**: ???

**critical_point_types**: id numbers of commonly(?) associated point types (look up in client.get_all_point_types())

**sub_types**: embedded JSON of possible forms of the generic equipment type (e.g. 'fan' has the sub types 'exhaustFan', 'reliefFan', 'returnFan', etc.)

**tags**: ???

Sub-equipment types
-------------------
Accessed for given equipment (e.g. 'fan') with :code:`sub_type = pd.DataFrame(equip_type[equip_type.tag_name == 'fan']['sub_types'].item())`

**id**: unique integer associated with the given type/tag

**equipment_type_id**: id of the associated equipment tag in client.get_equipment_types()

**tag_name**: short name generally used in scripts

**name_long**: longer, human-readable name

**name_abbr**: common abbreviated form

Point types
-----------
Accessed with :code:`client.get_all_point_types()`

**id**: unique integer associated with the given type/tag

**tag_name**: short name generally used in scripts

**display_name**:

**active**: ???

**measurement_id**: id of the associated measurement type in :code:`client.get_all_measurements()`

**tag_set_ids**: ???

**tags**: ???

**default_unit_id**: ??? (always None)

Unit types
----------
Accessed with :code:`pd.DataFrame(client.get_all_units())`

**id**: unique integer associated with the given type/tag

**name_long**: human-readable unit name (e.g. 'Cubic Meter per Hour')

**name_abbr**: abbreviated form (e.g. 'm3/h')

**data_type**: form of associated data. Can be 'Binary', 'Continuous', 'Enum', 'None', 'Ordinal'. ???

**raw_encoding**: for Binary and Enum data types, contains dictionary matching number to interpretation. ???

**display_encoding**: for Binary and Enum data types, contains dictionary showing how each reported number will be displayed. E.g., a 0 from an Occupancy sensor will be reported as ''Unoccupied'.

**qudt**:  url for additional information about unit (e.g. 'Degrees Celsius') on qudt.org

**unit_type**: url for additional information about measurement type (e.g. 'Temperature') on qudt.org

Measurement types
-----------------
Accessed with :code:`pd.DataFrame(client.get_all_measurements())`

**id**: unique integer associated with the given measurement types

**name**: name of measurement type

**default_unit_id**: id of associated unit types in client.get_all_units(). Note, pandas will cast this column as a float, but it can still be used to look up ids. (??? But why does Temperature, which contains all the temp units, just point to F? and why a float?)

**units_convertible**: True if units of this measurement type can be interchangeably converted (generally True for continuous measurement types)

**units**: embedded JSON of possible units for given measurement type

**qudt_type**: url for additional information about measurement type (e.g. 'Temperature') on qudt.org

Tag metadata
------------
Accessed with :code:`pd.DataFrame(client.get_tags())`

**id**: unique integer associated with the given tag metadata

**name**: name of tag being described

**definition**: definition of tag

**def_source**: source of definition (either brick, haystack, or onboard)

**def_url**: url for source of definition (brick and haystack only)

**category**: can be 'Medium', 'Medium Property', None, 'Point Class', 'Quantity Modifier' ???
