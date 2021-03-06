add_pyclif_library("properties" properties.clif)

add_pyclif_library("_symbol_table" symbol-table.clif
  LIBRARIES fst
)

add_pyclif_library("_weight" weight.clif)

add_pyclif_library("_float_weight" float-weight.clif
  CLIF_DEPS _weight
)

add_pyclif_library("_lattice_weight" lattice-weight.clif
  NAMESPACES fst
  CLIF_DEPS _float_weight
  LIBRARIES kaldi-base
)

add_pyclif_library("_lexicographic_weight" lexicographic-weight.clif
  CLIF_DEPS _float_weight
  LIBRARIES fst
)

add_pyclif_library("_arc" arc.clif
  NAMESPACES fst
  CLIF_DEPS _lattice_weight _lexicographic_weight
)

add_pyclif_library("_fst" fst.clif
  NAMESPACES fst
  CLIF_DEPS _arc _symbol_table _iostream
)

add_pyclif_library("_expanded_fst" expanded-fst.clif
  NAMESPACES fst
  CLIF_DEPS _fst
)

add_pyclif_library("_mutable_fst" mutable-fst.clif
  NAMESPACES fst
  CLIF_DEPS _arc _symbol_table
)

add_pyclif_library("_vector_fst" vector-fst.clif
  NAMESPACES fst
  CLIF_DEPS _fst _iostream
)

add_pyclif_library("_const_fst" const-fst.clif
  NAMESPACES fst
  CLIF_DEPS _fst _iostream
)

add_pyclif_library("_context_fst" context-fst.clif
  NAMESPACES fst fst::internal
  CLIF_DEPS _fst
)

add_pyclif_library("_context_fst_inl" context-fst-inl.clif
  CLIF_DEPS _symbol_table _iostream
  LIBRARIES kaldi-base
)

add_pyclif_library("_deterministic_fst" deterministic-fst.clif
  NAMESPACES fst
  CLIF_DEPS _fst _mutable_fst
)

add_pyclif_library("_lattice_utils" lattice-utils.clif)

add_pyclif_library("_determinize_lattice" determinize-lattice.clif)

add_pyclif_library("_push_special" push-special.clif
  NAMESPACES fst
  CLIF_DEPS _vector_fst
  LIBRARIES kaldi-fstext
)

add_pyclif_library("_table_matcher" table-matcher.clif
  NAMESPACES fst
  CLIF_DEPS _getters _fst _mutable_fst
)

add_pyclif_library("_fstext_shims" fstext-shims.clif
  CLIF_DEPS _iostream _expanded_fst _mutable_fst _vector_fst _const_fst
  LIBRARIES kaldi-fstext
)

add_pyclif_library("_fstext_utils" fstext-utils.clif
  CLIF_DEPS _vector_fst
  LIBRARIES kaldi-fstext
)

add_pyclif_library("_fstext_utils_inl" fstext-utils-inl.clif
  NAMESPACES fst
  CLIF_DEPS _mutable_fst _vector_fst
  LIBRARIES kaldi-fstext
)

add_pyclif_library("_drawer" drawer.clif
  CLIF_DEPS _fst _iostream
)

add_pyclif_library("_printer" printer.clif
  CLIF_DEPS _fst _iostream
)

add_pyclif_library("_compiler" compiler.clif
  CLIF_DEPS _vector_fst _iostream
)

add_pyclif_library("_getters" getters.clif
  LIBRARIES fstscript
)

add_pyclif_library("_encode" encode.clif
  CLIF_DEPS _iostream _getters _symbol_table _arc
  NAMESPACES fst
)

add_pyclif_library("_std_ops" std-ops.clif
  CLIF_DEPS _getters _encode _mutable_fst _vector_fst
  NAMESPACES fst
)

add_pyclif_library("_log_ops" log-ops.clif
  CLIF_DEPS _getters _encode _mutable_fst _vector_fst
  NAMESPACES fst
)

add_pyclif_library("_lat_ops" lat-ops.clif
  CLIF_DEPS _getters _encode _mutable_fst _vector_fst
  NAMESPACES fst
)

add_pyclif_library("_clat_ops" clat-ops.clif
  CLIF_DEPS _getters _encode _mutable_fst _vector_fst
  NAMESPACES fst
)

add_pyclif_library("_index_ops" index-ops.clif
  CLIF_DEPS _getters _encode _mutable_fst _vector_fst
  NAMESPACES fst
)

add_pyclif_library("_special_ops" special-ops.clif
  CLIF_DEPS _getters _mutable_fst _vector_fst _context_fst _deterministic_fst _determinize_lattice
  NAMESPACES fst
)
