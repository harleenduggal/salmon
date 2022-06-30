#!/usr/bin/env nextflow
params.bam = ""
params.outdir = ""
params.transcriptome = ""


process salmon_quant{
   publishDir params.outdir

   input:

   file transcriptome from file(params.transcriptome)
   file bam from file(params.bam)
   output:
   file ("salmon_quant") into qunat_ch

   """
   mkdir salmon_quant
   salmon quant -t $transcriptome  -l A  -a $bam  -o salmon_quant
   """
}
