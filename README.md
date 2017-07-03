# onettersqlcodes
CREATE TABLE occupation_level_metadata (   onetsoc_code CHARACTER(10) NOT NULL,   item CHARACTER VARYING(150) NOT NULL,   response CHARACTER VARYING(75),   n DECIMAL(4,0),   percent DECIMAL(4,1),   date_updated DATE NOT NULL,   FOREIGN KEY (onetsoc_code) REFERENCES occupation_data(onetsoc_code));


CREATE TABLE abilities (
  onetsoc_code CHARACTER(10) NOT NULL,
  element_id CHARACTER VARYING(20) NOT NULL,
  scale_id CHARACTER VARYING(3) NOT NULL,
  data_value DECIMAL(5,2) NOT NULL,
  n DECIMAL(4,0),
  standard_error DECIMAL(5,2),
  lower_ci_bound DECIMAL(5,2),
  upper_ci_bound DECIMAL(5,2),
  recommend_suppress CHARACTER(1),
  not_relevant CHARACTER(1),
  date_updated DATE NOT NULL,
  domain_source CHARACTER VARYING(30) NOT NULL,
  FOREIGN KEY (onetsoc_code) REFERENCES occupation_data(onetsoc_code),
  FOREIGN KEY (element_id) REFERENCES content_model_reference(element_id),
  FOREIGN KEY (scale_id) REFERENCES scales_reference(scale_id));
  
  CREATE TABLE education_training_experience (
  onetsoc_code CHARACTER(10) NOT NULL,
  element_id CHARACTER VARYING(20) NOT NULL,
  scale_id CHARACTER VARYING(3) NOT NULL,
  category DECIMAL(3,0),
  data_value DECIMAL(5,2) NOT NULL,
  n DECIMAL(4,0),
  standard_error DECIMAL(5,2),
  lower_ci_bound DECIMAL(5,2),
  upper_ci_bound DECIMAL(5,2),
  recommend_suppress CHARACTER(1),
  date_updated DATE NOT NULL,
  domain_source CHARACTER VARYING(30) NOT NULL,
  FOREIGN KEY (onetsoc_code) REFERENCES occupation_data(onetsoc_code),
  FOREIGN KEY (element_id) REFERENCES content_model_reference(element_id),
  FOREIGN KEY (scale_id) REFERENCES scales_reference(scale_id),
  FOREIGN KEY (element_id, scale_id, category) REFERENCES ete_categories(element_id, scale_id, category));

CREATE TABLE emerging_tasks (
  onetsoc_code CHARACTER(10) NOT NULL,
  task CHARACTER VARYING(1000) NOT NULL,
  category CHARACTER VARYING(8) NOT NULL,
  original_task_id DECIMAL(8,0),
  writein_total DECIMAL(3,0) NOT NULL,
  date_updated DATE NOT NULL,
  domain_source CHARACTER VARYING(30) NOT NULL,
  FOREIGN KEY (onetsoc_code) REFERENCES occupation_data(onetsoc_code),
  FOREIGN KEY (original_task_id) REFERENCES task_statements(task_id));
  
  CREATE TABLE career_changers_matrix (
  onetsoc_code CHARACTER(10) NOT NULL,
  related_onetsoc_code CHARACTER(10) NOT NULL,
  related_index DECIMAL(3,0) NOT NULL,
  FOREIGN KEY (onetsoc_code) REFERENCES occupation_data(onetsoc_code),
  FOREIGN KEY (related_onetsoc_code) REFERENCES occupation_data(onetsoc_code));
