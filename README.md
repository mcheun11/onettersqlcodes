# onettersqlcodes
CREATE TABLE occupation_level_metadata (   onetsoc_code CHARACTER(10) NOT NULL,   item CHARACTER VARYING(150) NOT NULL,   response CHARACTER VARYING(75),   n DECIMAL(4,0),   percent DECIMAL(4,1),   date_updated DATE NOT NULL,   FOREIGN KEY (onetsoc_code) REFERENCES occupation_data(onetsoc_code));
