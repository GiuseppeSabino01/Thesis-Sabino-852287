Il notebook è diviso in "sezioni" in maniera tale da avere un ordine al suo interno.

Le sezioni "Import Library" e "Function" sono essenziali per lo svolgimento.

La sezione "Import Data" importa i dataset tradotti direttamente da drive, in questo modo si può saltare la parte di traduzione che risultava onerosa in tempi computazionali. Bisogna fare attenzione per il dataset DepSeverity in quanto ci sono due possibili task da affrontare(binario, multiclass).

All' interno delle sezioni "Dreaddit", "DepSeverity" e "SDCNL" è contenuto una breve parte di data exploration.

La sezione "Combine DF" è utile nel caso in cui si volessero unire i dataset per l'approccio di creazione dei modelli italiani generalizzati.

La sezione "Traduzione" può essere saltata se si importano i dati direttamente dalla sezione "Import Data".

Le susseguenti sezioni con i nomi dei modelli rappresentano elaborazioni fine-tuning. Viene importato il modello da HG, viene effettuato l'allenamento e salvati i pesi in una cartella drive. Dopo aver caricato i pesi (pensato per elaborazioni a distanza di tempo) viene effettuato una fase di test. Bisogna cambiare manualmente il codice in base al dataset su cui si sta allenando/testando. Se genera errore per Qwen2 0.5B e Flan-T5, controllare e assegnare batch_size = 1

Stesso discorso vale per le elaborazioni CrossLanguage. Flan-T5 e Qwn2 0.5B non hanno necessità di essere riallenate in quanto multilingue (vengono usati i pesi salvati precedentemente). Per BERT e RoBERTa è invece necessaria una fase di allenamento.

Per le elaborazioni zero-shot, bisogna selezionare la "question_prompt" adatta in base al dataset di utilizzo. è anche necessario inserire manualmente il dataset dove evidenziato dai commenti. In base al tipo di problema (binario o multiclass) è necessario aggiornare le euristiche e la funzione di calcolo della balanced_accuracy.

Dataset.
All'interno della cartella dataset sono presenti sia le versioni originali che tradotte.
sdcnl_test_tradotto, sdcnl_train_tradotto, dreaddit_train_tradotto, dreaddit_test_tradotto, dep_severity_tradotto sono le versioni italiane che importo direttamente da drive nella sezione "Import Data".