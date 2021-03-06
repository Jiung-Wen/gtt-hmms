# gtt-hmms for _Bacteroidetes_ and _Bacteroidaceae_
Custom single copy gene (SCG)-set HMMs for [GToTree](https://github.com/AstrobioMike/GToTree) (a user-friendly workflow for phylogenomics).


## Example usage
**Note**: It is assumed that GToTree is properly installed.  

Put the hmm files in hmm_sets to the path you see by running ```gtt-hmms``` and then run GToTree normally:

```bash
GToTree -a ncbi_accssion.txt \
        -H Bacteroidetes_2022-04 \
        -j 4 \
        -o output
```

## Downloading complete genomes (accessed on April 25, 2022)
The complete genomes were downloaded using the following commands:
```bash
# phylum Bacteroidetes
esearch -query '"bacteria"[filter] AND ("Bacteroidetes"[Organism] OR "Bacteroidia"[Organism]) AND "Complete genome"[filter] AND latest[filter] NOT anomalous[filter] AND "has annotation"[Properties]' -db assembly | esummary | xtract -pattern DocumentSummary -def "NA" -element AssemblyAccession Taxid SpeciesTaxid Organism AssemblyStatus RefSeq_category FtpPath_GenBank FtpPath_RefSeq FtpPath_Assembly_rpt > Complete_genome_bacteroidetes_ncbi_info.tsv
```

```bash
# family Bacteroidaceae
esearch -query '"bacteria"[filter] AND "Bacteroidaceae"[ORGN] AND "Complete genome"[filter] AND latest[filter] NOT anomalous[filter] AND "has annotation"[Properties]' -db assembly | esummary | xtract -pattern DocumentSummary -def "NA" -element AssemblyAccession Taxid SpeciesTaxid Organism AssemblyStatus RefSeq_category FtpPath_GenBank FtpPath_RefSeq FtpPath_Assembly_rpt > Complete_genome_bacteroidaceae_ncbi_info.tsv
```
As a result, 1,053 and 99 complete genome assemblies for _Bacteroidetes_ and _Bacteroidaceae_, respectively, were downloaded from NCBI database.

## Generating custom single-copy genes (SCGs) hidden Markov models
The steps and code used to generate the HMMs were as described in [GToTree's tutorial](https://github.com/AstrobioMike/GToTree/wiki/SCG-sets), except that 9,892 Pfams with coverage greater than 50% out of all 19,632 Pfams from release 35.0 were searched against.

---

## SCGs for phylogenomic tree reconstruction
| Target taxa | # of genes | pfam names |
| :---: | :---: | ---|
| phylum _Bacteroidetes_ | 112 | 5-FTHF_cyc-lig, Actin, ADK, AIRC, ATP-synt, ATP-synt_A, ATP-synt_B, ATP-synt_DE_N, BacA, Chorismate_synt, Cpn60_TCP1, Cytidylate_kin, DHquinase_II, DMRL_synthase, DUF2795, DUF3109, DUF3467, DUF4290, DUF4293, DUF4295, EF_TS, eIF-1a, FolB, FtsL_2, GidB, GrpE, Ham1p_like, LptE, LpxC, Lum_binding, Maf, Methyltransf_5, MnmE_helical, MreC, OSCP, PdxA, Pept_tRNA_hydro, PGK, Porin_10, Prenyltransf, RBFA, RecX, Ribonuclease_P, Ribosom_S12_S23, Ribosomal_L1, Ribosomal_L13, Ribosomal_L14, Ribosomal_L16, Ribosomal_L17, Ribosomal_L18p, Ribosomal_L19, Ribosomal_L20, Ribosomal_L21p, Ribosomal_L22, Ribosomal_L23, ribosomal_L24, Ribosomal_L27, Ribosomal_L27A, Ribosomal_L28, Ribosomal_L29, Ribosomal_L3, Ribosomal_L31, Ribosomal_L32p, Ribosomal_L33, Ribosomal_L34, Ribosomal_L35p, Ribosomal_L36, Ribosomal_L4, Ribosomal_L6, Ribosomal_L9_C, Ribosomal_S10, Ribosomal_S11, Ribosomal_S13, Ribosomal_S14, Ribosomal_S15, Ribosomal_S17, Ribosomal_S19, Ribosomal_S2, Ribosomal_S20p, Ribosomal_S21, Ribosomal_S6, Ribosomal_S7, Ribosomal_S8, Ribosomal_S9, Ribul_P_3_epim, RNA_pol_L, RNA_pol_Rpb6, RNase_HII, RRF, RsfS, RuvX, SAICAR_synt, SecE, SecG, SecY, SmpB, SufE, SurE, TGT, TIM, Transcrip_reg, tRNA_m1G_MT, tRNA-synt_1d, tRNA-synt_1e, tRNA-synt_2c, tRNA-synt_His, UPF0102, YajC, YbeY, YceD, YicC_N, ZapA |
| family _Bacteroidaceae_ | 328 | 5-FTHF_cyc-lig, 6PGD, Actin, Acyltransf_2, Adenylsucc_synt, ADK, AIRC, Aldolase, Arginosuc_synth, AsnA, Asp_decarbox, Asp_Glu_race, ATP-synt, ATP-synt_A, ATP-synt_B, ATP-synt_D, ATP-synt_DE_N, BacA, BFN_dom, C_GCAxxG_C_C, Chorismate_synt, CinA, Citrate_synt, CoaE, Colicin_V, Complex1_49kDa, Cpn10, Cpn60_TCP1, CRCB, CSD, CstA, Cu-oxidase_4, CutC, Cyt_bd_oxida_I, Cyt_bd_oxida_II, CYTH, Cytidylate_kin, Dabb, DAP_epimerase, DapB_C, DciA, DcuA_DcuB, DHFR_1, DHQ_synthase, DHquinase_II, DivIC, DMRL_synthase, DMT_6, DNA_pol3_delta, DrsE, DUF1015, DUF1295, DUF1460, DUF1599, DUF179, DUF2461, DUF2721, DUF2764, DUF2795, DUF2851, DUF3108, DUF3109, DUF3256, DUF3316, DUF3332, DUF3467, DUF3700, DUF3737, DUF3805, DUF3810, DUF3822, DUF417, DUF4199, DUF4250, DUF4271, DUF4286, DUF4290, DUF4292, DUF4293, DUF4294, DUF4295, DUF4301, DUF4348, DUF4375, DUF4491, DUF4492, DUF452, DUF454, DUF4827, DUF4831, DUF4834, DUF4836, DUF4837, DUF4847, DUF4924, DUF4954, DUF5056, DUF5063, DUF5683, DUF5687, DUF5715, DUF6048, DUF6064, DUF6340, DUF6452, DUF6621, dUTPase, EF_TS, eIF-1a, Exonuc_VII_L, Exonuc_VII_S, F_bP_aldolase, FAA_hydrolase, FBPase_2, Flavoprotein, FloA, FolB, FTCD_C, FTHFS, FtsL_2, Fumerase, G6PD_C, GcpE, GCV_H, GDC-P, GGGtGRT, GH3, GidB, GldH_lipo, Gly_transporter, Glyco_hydro_25, Glyco_hydro_57, Glyco_hydro_77, Glycogen_syn, Glycos_transf_3, GSCFA, GTP_cyclohydroI, H_PPase, H2O2_YaaD, Ham1p_like, HEM4, HisG, Histidinol_dh, HlyIII, HTS, IGPD, IGPS, ILVD_EDD, KdpA, KdpC, LacAB_rpiB, LolA_2, LptC, LptE, LpxB, LpxC, LpxK, LrgA, LrgB, Lum_binding, LysE, LYTB, Maf, MerR_2, META, Methyltrans_RNA, Methyltrans_SAM, Methyltransf_5, MlaE, MnmE_helical, Mntp, MraZ, MreC, Na_Ca_ex, NadA, NADHdh, NIF3, NMN_transporter, Nuc_H_symport, OMPdecase, OPT, OSCP, Oxidored_FMN, Oxidored_q2, Oxidored_q3, Oxidored_q4, Oxidored_q6, Pan_kinase, Pantoate_ligase, Pantoate_transf, PDT, PdxA, PdxJ, Pep_deformylase, PEPCK_ATP, Pept_tRNA_hydro, Peptidase_A8, Peptidase_M13_N, Peptidase_M15, Peptidase_M49, Peptidase_S13, PGI, PGK, Phage_holin_3_6, PK, PMSR, Porin_10, PRAI, Prenyltransf, Prismane, Pro_CA, PS_Dcarbxylase, PTPS, PyrI, Pyridoxal_deC, QRPTase_C, Rad51, RBFA, RE_HpaII, RecA, RecO_C, RecX, Ribonuclease_P, Ribosom_S12_S23, Ribosomal_L1, Ribosomal_L13, Ribosomal_L14, Ribosomal_L16, Ribosomal_L17, Ribosomal_L18p, Ribosomal_L19, Ribosomal_L20, Ribosomal_L21p, Ribosomal_L22, Ribosomal_L23, ribosomal_L24, Ribosomal_L27, Ribosomal_L27A, Ribosomal_L28, Ribosomal_L29, Ribosomal_L3, Ribosomal_L31, Ribosomal_L32p, Ribosomal_L33, Ribosomal_L34, Ribosomal_L35p, Ribosomal_L36, Ribosomal_L4, Ribosomal_L6, Ribosomal_L9_C, Ribosomal_S10, Ribosomal_S11, Ribosomal_S13, Ribosomal_S14, Ribosomal_S15, Ribosomal_S17, Ribosomal_S19, Ribosomal_S2, Ribosomal_S20p, Ribosomal_S21, Ribosomal_S30AE, Ribosomal_S6, Ribosomal_S7, Ribosomal_S8, Ribosomal_S9, Ribul_P_3_epim, RmuC, RNA_pol_L, RNA_pol_Rpb6, RNase_HII, RRF, RseC_MucC, RsfS, RuvC, RuvX, S4_2, Sacchrp_dh_C, SAICAR_synt, SBP_bac_6, SBP_bac_8, SecE, SecG, SecY, SHMT, SIR2, SmpB, SNF, SNO, SPOUT_MTase, START_2, SufE, Sulfate_transp, Sulfotransfer_1, SurE, TAL_FSA, TGT, ThiC_Rad_SAM, ThiS, TK, Transcrip_reg, tRNA_m1G_MT, tRNA-synt_1d, tRNA-synt_1e, tRNA-synt_2c, tRNA-synt_His, Trp_syntA, Tyr_Deacylase, UPF0014, UPF0102, UPRTase, UxaC, V_ATPase_I, VanZ, Vut_1, YajC, YbeY, YceD, YceG, YfhO, YgbA_NO, YgbB, YgjP-like, YicC_N, YidD, YqeY, ZapA, Zn_peptidase_2, ZnuA |
