# Análisis de anotaciones de circuitos significativos a individuos, según variantes identificadas sin filtrar por CADD


###################################################################################################################################################

### 1 - Selección de variantes desde IVA Outputs y creación de listado de genes por ind ###

script -> Var_NoCADD.R ("/home/ampergut/CBRA/projects/TFM/kos_GTEX/new_analysis_140720/allVariants_NoCADD/")
	- Input -> tablas de variantes (outputs IVA)
	- Output -> listas de genes (gene SIMBOL) por individuo:
		-> en heterocigosis --> "/home/ampergut/CBRA/projects/TFM/kos_GTEX/new_analysis_140720/inheritance_model/HetVar/het_gene_lists/"
		-> en homocigosis --> "/home/ampergut/CBRA/projects/TFM/kos_GTEX/new_analysis_140720/inheritance_model/HomVar/hom_gene_lists/"
		
###################################################################################################################################################


### 2 - conversión a 'entrezid' y conteos de cuántas variantes en cada gen ###

script 
-> het_freq_tables.R ("/home/ampergut/CBRA/projects/TFM/kos_GTEX/new_analysis_140720/inheritance_model/HetVar/")
-> hom_freq_tables.R ("/home/ampergut/CBRA/projects/TFM/kos_GTEX/new_analysis_140720/inheritance_model/HomVar/")
	- Input -> Outputs PASO 1
	- Output -> listas de genes (gene SIMBOL) por individuo:
		-> en heterocigosis --> "/home/ampergut/CBRA/projects/TFM/kos_GTEX/new_analysis_140720/inheritance_model/HetVar/het_gene_tbs/"
		-> en homocigosis --> "/home/ampergut/CBRA/projects/TFM/kos_GTEX/new_analysis_140720/inheritance_model/HomVar/hom_gene_tbs/"
		
###################################################################################################################################################


### 3 - Organización de ficheros por individuo - hecho con comandos de bash (no está todo automatizado) ###
"/home/ampergut/CBRA/projects/TFM/kos_GTEX/new_analysis_140720/inheritance_model/ind"



###################################################################################################################################################

### 4 - Creación de tablas de genes por individuo en R ###

script -> ind_str.R ("/home/ampergut/CBRA/projects/TFM/kos_GTEX/new_analysis_140720/inheritance_model/")
	- Input -> ficheros /ind (PASO 3)
	- Output -> tablas_NoCADD.rds ("script ->inheritance_model/")
	


###################################################################################################################################################



### 5 - Anotación genes a los circuitos significativos ###

script -> gene_list_sigcircuits.R ("/home/ampergut/CBRA/projects/TFM/kos_GTEX/new_analysis_140720/functional_analysis/geneList_sigCircuit/")
	- Input -> DBpv.comb.3m.byrow.sel.id.path.ann.rds (TFM ANALYSIS)
	("/media/ampergut/EA3A4CE53A4CB07D/amperez/projects/TFM/result_report/DBpv.comb.3m.byrow.sel.id.path.ann.rds")
	- Output -> sig_pathways_DM/AM_genelist ("/home/ampergut/CBRA/projects/TFM/kos_GTEX/new_analysis_140720/functional_analysis/geneList_sigCircuit/")




###################################################################################################################################################


### 6 - Anotación de circuitos significativos (análisis TFM) a cada individuo ###


script -> listado_annot_ind_sig.ciscuit_NOCADD.R ("/home/ampergut/CBRA/projects/TFM/kos_GTEX/new_analysis_140720/inheritance_model/circuits_ann/")
	- Input -> sig_pathways_DM/AM_genelist (Output anterior, PASO 5)
	- Output -> PENDIENTE DE ORGANIZAR




###################################################################################################################################################












