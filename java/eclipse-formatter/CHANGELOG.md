# Change Log

## [0.1.0] - 2022-12-14

### Added

Javaのバージョンアップに伴い、Eclipseのフォーマッターも設定項目が更新されています。

`Eclipse Version 2022-6`の設定項目とNablarchのフォーマッター設定ファイルを比較し、次の項目を追加しました。

```xml
<setting id="org.eclipse.jdt.core.formatter.align_with_spaces" value="false"/>
<setting id="org.eclipse.jdt.core.formatter.number_of_blank_lines_before_code_block" value="0"/>
<setting id="org.eclipse.jdt.core.formatter.insert_space_before_comma_in_switch_case_expressions" value="donotinsert"/>
<setting id="org.eclipse.jdt.core.formatter.alignment_for_record_components" value="16"/>
<setting id="org.eclipse.jdt.core.formatter.wrap_before_multiplicative_operator" value="true"/>
<setting id="org.eclipse.jdt.core.formatter.alignment_for_logical_operator" value="16"/>
<setting id="org.eclipse.jdt.core.formatter.keep_annotation_declaration_on_one_line" value="one_line_never"/>
<setting id="org.eclipse.jdt.core.formatter.insert_space_before_closing_paren_in_record_declaration" value="donotinsert"/>
<setting id="org.eclipse.jdt.core.formatter.insert_space_after_multiplicative_operator" value="insert"/>
<setting id="org.eclipse.jdt.core.formatter.blank_lines_before_abstract_method" value="1"/>
<setting id="org.eclipse.jdt.core.formatter.keep_enum_constant_declaration_on_one_line" value="one_line_never"/>
<setting id="org.eclipse.jdt.core.formatter.align_variable_declarations_on_columns" value="false"/>
<setting id="org.eclipse.jdt.core.formatter.alignment_for_multiplicative_operator" value="16"/>
<setting id="org.eclipse.jdt.core.formatter.keep_anonymous_type_declaration_on_one_line" value="one_line_never"/>
<setting id="org.eclipse.jdt.core.formatter.insert_space_after_comma_in_switch_case_expressions" value="insert"/>
<setting id="org.eclipse.jdt.core.formatter.wrap_before_shift_operator" value="true"/>
<setting id="org.eclipse.jdt.core.formatter.number_of_blank_lines_at_end_of_code_block" value="0"/>
<setting id="org.eclipse.jdt.core.formatter.insert_space_before_bitwise_operator" value="insert"/>
<setting id="org.eclipse.jdt.core.formatter.alignment_for_compact_loops" value="16"/>
<setting id="org.eclipse.jdt.core.formatter.keep_simple_for_body_on_same_line" value="false"/>
<setting id="org.eclipse.jdt.core.formatter.wrap_before_switch_case_arrow_operator" value="false"/>
<setting id="org.eclipse.jdt.core.formatter.alignment_for_annotations_on_enum_constant" value="49"/>
<setting id="org.eclipse.jdt.core.formatter.text_block_indentation" value="0"/>
<setting id="org.eclipse.jdt.core.formatter.comment.align_tags_names_descriptions" value="false"/>
<setting id="org.eclipse.jdt.core.formatter.keep_if_then_body_block_on_one_line" value="one_line_never"/>
<setting id="org.eclipse.jdt.core.formatter.align_assignment_statements_on_columns" value="false"/>
<setting id="org.eclipse.jdt.core.formatter.insert_space_before_comma_in_permitted_types" value="donotinsert"/>
<setting id="org.eclipse.jdt.core.formatter.alignment_for_conditional_expression_chain" value="0"/>
<setting id="org.eclipse.jdt.core.formatter.alignment_for_type_annotations" value="0"/>
<setting id="org.eclipse.jdt.core.formatter.wrap_before_assertion_message_operator" value="true"/>
<setting id="org.eclipse.jdt.core.formatter.alignment_for_bitwise_operator" value="16"/>
<setting id="org.eclipse.jdt.core.formatter.insert_space_after_not_operator" value="donotinsert"/>
<setting id="org.eclipse.jdt.core.formatter.alignment_for_annotations_on_package" value="49"/>
<setting id="org.eclipse.jdt.core.formatter.insert_space_after_arrow_in_switch_case" value="insert"/>
<setting id="org.eclipse.jdt.core.formatter.indent_body_declarations_compare_to_record_header" value="true"/>
<setting id="org.eclipse.jdt.core.formatter.wrap_before_bitwise_operator" value="true"/>
<setting id="org.eclipse.jdt.core.formatter.comment.indent_tag_description" value="false"/>
<setting id="org.eclipse.jdt.core.formatter.brace_position_for_record_constructor" value="end_of_line"/>
<setting id="org.eclipse.jdt.core.formatter.alignment_for_string_concatenation" value="16"/>
<setting id="org.eclipse.jdt.core.formatter.insert_space_before_shift_operator" value="insert"/>
<setting id="org.eclipse.jdt.core.formatter.insert_space_after_shift_operator" value="insert"/>
<setting id="org.eclipse.jdt.core.formatter.keep_simple_do_while_body_on_same_line" value="false"/>
<setting id="org.eclipse.jdt.core.formatter.insert_space_before_comma_in_record_components" value="donotinsert"/>
<setting id="org.eclipse.jdt.core.formatter.wrap_before_additive_operator" value="true"/>
<setting id="org.eclipse.jdt.core.formatter.keep_simple_getter_setter_on_one_line" value="false"/>
<setting id="org.eclipse.jdt.core.formatter.insert_space_before_string_concatenation" value="insert"/>
<setting id="org.eclipse.jdt.core.formatter.insert_space_before_opening_paren_in_record_declaration" value="donotinsert"/>
<setting id="org.eclipse.jdt.core.formatter.insert_space_after_relational_operator" value="insert"/>
<setting id="org.eclipse.jdt.core.formatter.insert_space_after_logical_operator" value="insert"/>
<setting id="org.eclipse.jdt.core.formatter.parentheses_positions_in_record_declaration" value="common_lines"/>
<setting id="org.eclipse.jdt.core.formatter.insert_space_after_arrow_in_switch_default" value="insert"/>
<setting id="org.eclipse.jdt.core.formatter.number_of_blank_lines_at_end_of_method_body" value="0"/>
<setting id="org.eclipse.jdt.core.formatter.insert_space_before_arrow_in_switch_case" value="insert"/>
<setting id="org.eclipse.jdt.core.formatter.keep_switch_body_block_on_one_line" value="one_line_never"/>
<setting id="org.eclipse.jdt.core.formatter.alignment_for_expressions_in_switch_case_with_arrow" value="0"/>
<setting id="org.eclipse.jdt.core.formatter.comment.align_tags_descriptions_grouped" value="false"/>
<setting id="org.eclipse.jdt.core.formatter.keep_method_body_on_one_line" value="one_line_never"/>
<setting id="org.eclipse.jdt.core.formatter.keep_loop_body_block_on_one_line" value="one_line_never"/>
<setting id="org.eclipse.jdt.core.formatter.keep_type_declaration_on_one_line" value="one_line_never"/>
<setting id="org.eclipse.jdt.core.formatter.alignment_for_additive_operator" value="16"/>
<setting id="org.eclipse.jdt.core.formatter.insert_space_before_opening_brace_in_record_constructor" value="insert"/>
<setting id="org.eclipse.jdt.core.formatter.insert_space_before_relational_operator" value="insert"/>
<setting id="org.eclipse.jdt.core.formatter.keep_record_declaration_on_one_line" value="one_line_never"/>
<setting id="org.eclipse.jdt.core.formatter.alignment_for_annotations_on_parameter" value="0"/>
<setting id="org.eclipse.jdt.core.formatter.alignment_for_relational_operator" value="0"/>
<setting id="org.eclipse.jdt.core.formatter.insert_space_after_additive_operator" value="insert"/>
<setting id="org.eclipse.jdt.core.formatter.insert_space_after_string_concatenation" value="insert"/>
<setting id="org.eclipse.jdt.core.formatter.align_selector_in_method_invocation_on_expression_first_line" value="false"/>
<setting id="org.eclipse.jdt.core.formatter.brace_position_for_record_declaration" value="end_of_line"/>
<setting id="org.eclipse.jdt.core.formatter.keep_switch_case_with_arrow_on_one_line" value="one_line_never"/>
<setting id="org.eclipse.jdt.core.formatter.alignment_for_expressions_in_switch_case_with_colon" value="0"/>
<setting id="org.eclipse.jdt.core.formatter.number_of_blank_lines_after_code_block" value="0"/>
<setting id="org.eclipse.jdt.core.formatter.alignment_for_annotations_on_type" value="49"/>
<setting id="org.eclipse.jdt.core.formatter.alignment_for_annotations_on_local_variable" value="49"/>
<setting id="org.eclipse.jdt.core.formatter.insert_space_before_arrow_in_switch_default" value="insert"/>
<setting id="org.eclipse.jdt.core.formatter.comment.insert_new_line_between_different_tags" value="donotinsert"/>
<setting id="org.eclipse.jdt.core.formatter.insert_space_before_additive_operator" value="insert"/>
<setting id="org.eclipse.jdt.core.formatter.alignment_for_annotations_on_field" value="49"/>
<setting id="org.eclipse.jdt.core.formatter.alignment_for_shift_operator" value="0"/>
<setting id="org.eclipse.jdt.core.formatter.keep_code_block_on_one_line" value="one_line_never"/>
<setting id="org.eclipse.jdt.core.formatter.insert_space_after_comma_in_record_components" value="insert"/>
<setting id="org.eclipse.jdt.core.formatter.insert_space_after_bitwise_operator" value="insert"/>
<setting id="org.eclipse.jdt.core.formatter.insert_space_after_opening_paren_in_record_declaration" value="donotinsert"/>
<setting id="org.eclipse.jdt.core.formatter.alignment_for_switch_case_with_arrow" value="0"/>
<setting id="org.eclipse.jdt.core.formatter.keep_lambda_body_block_on_one_line" value="one_line_never"/>
<setting id="org.eclipse.jdt.core.formatter.alignment_for_annotations_on_method" value="49"/>
<setting id="org.eclipse.jdt.core.formatter.keep_record_constructor_on_one_line" value="one_line_never"/>
<setting id="org.eclipse.jdt.core.formatter.insert_space_before_opening_brace_in_record_declaration" value="insert"/>
<setting id="org.eclipse.jdt.core.formatter.alignment_for_assertion_message" value="0"/>
<setting id="org.eclipse.jdt.core.formatter.insert_space_before_logical_operator" value="insert"/>
<setting id="org.eclipse.jdt.core.formatter.alignment_for_superinterfaces_in_record_declaration" value="16"/>
<setting id="org.eclipse.jdt.core.formatter.wrap_before_relational_operator" value="true"/>
<setting id="org.eclipse.jdt.core.formatter.blank_lines_after_last_class_body_declaration" value="0"/>
<setting id="org.eclipse.jdt.core.formatter.keep_simple_while_body_on_same_line" value="false"/>
<setting id="org.eclipse.jdt.core.formatter.wrap_before_logical_operator" value="true"/>
<setting id="org.eclipse.jdt.core.formatter.blank_lines_between_statement_group_in_switch" value="0"/>
<setting id="org.eclipse.jdt.core.formatter.insert_space_after_comma_in_permitted_types" value="insert"/>
<setting id="org.eclipse.jdt.core.formatter.keep_enum_declaration_on_one_line" value="one_line_never"/>
<setting id="org.eclipse.jdt.core.formatter.insert_space_before_multiplicative_operator" value="insert"/>
<setting id="org.eclipse.jdt.core.formatter.number_of_blank_lines_at_beginning_of_code_block" value="0"/>
<setting id="org.eclipse.jdt.core.formatter.wrap_before_string_concatenation" value="true"/>
```