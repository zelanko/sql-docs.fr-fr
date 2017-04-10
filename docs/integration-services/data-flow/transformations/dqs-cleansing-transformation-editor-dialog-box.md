---
title: "&#201;diteur de transformation de nettoyage DQS (bo&#238;te de dialogue) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.ssdqs.designer.cleansing.f1"
  - "sql13.SSDQS.DESIGNER.DQCONNECTION.F1"
ms.assetid: 07e79641-71ee-45d0-a9ba-ed6f9f68f333
caps.latest.revision: 16
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 16
---
# &#201;diteur de transformation de nettoyage DQS (bo&#238;te de dialogue)
  Utilisez la boîte de dialogue de **l’Éditeur de transformation de nettoyage DQS** pour corriger les données à l’aide de DQS (Data Quality Services). Pour plus d’informations, consultez [Concepts Data Quality Services](../../../data-quality-services/data-quality-services-concepts.md).  
  
 Pour en savoir plus sur la transformation, consultez [Transformation de nettoyage DQS](../../../integration-services/data-flow/transformations/dqs-cleansing-transformation.md).  
  
 **Que voulez-vous faire ?**  
  
-   [Ouvrir l'Éditeur de transformation de nettoyage DQS](#open)  
  
-   [Définir les options de l'onglet Gestionnaires de connexions](#connection)  
  
-   [Définir les options sur l'onglet mappage](#mapping)  
  
-   [Définir les options de l'onglet Avancé](#advanced)  
  
-   [Définir les options dans la boîte de dialogue Gestionnaire de connexions du nettoyage DQS](#manager)  
  
##  <a name="open"></a> Ouvrir l'Éditeur de transformation de nettoyage DQS  
  
1.  Ajoutez la transformation de nettoyage DQS au package [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], dans [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].  
  
2.  Cliquez avec le bouton droit sur le composant, puis cliquez sur **Modifier**.  
  
##  <a name="connection"></a> Définir les options de l'onglet Gestionnaires de connexions  
 **Gestionnaire de connexions Data Quality Services**  
 Sélectionnez un gestionnaire de connexions DQS existant dans la liste, ou créez une connexion en cliquant sur **Nouveau**.  
  
 **Nouveau**  
 Créez un gestionnaire de connexions à l’aide de la boîte de dialogue **Gestionnaire de connexions du nettoyage DQS**. Consultez [Définir les options dans la boîte de dialogue Gestionnaire de connexions du nettoyage DQS](#manager)  
  
 **Base de connaissances Data Quality Services**  
 Sélectionnez une base de connaissances DQS existante pour la source de données connectée. Pour plus d’informations sur la base de connaissances DQS, consultez [Bases de connaissances et domaines DQS](../../../data-quality-services/dqs-knowledge-bases-and-domains.md).  
  
 **Chiffrer la connexion**  
 Spécifiez s’il faut chiffrer la connexion, afin de chiffrer le transfert des données entre le serveur DQS et [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].  
  
 **Champs disponibles**  
 Répertorie les champs disponibles pour la base de connaissances sélectionnée. Il existe deux types de champs : domaines uniques, et domaines composés qui contiennent au moins deux domaines uniques.  
  
 Pour plus d’informations sur la façon de mapper des colonnes à des domaines composites, consultez [Mapper des colonnes à des domaines composites](../../../integration-services/data-flow/transformations/map-columns-to-composite-domains.md).  
  
 Pour plus d’informations sur les domaines, consultez [Bases de connaissances et domaines DQS](../../../data-quality-services/dqs-knowledge-bases-and-domains.md).  
  
 **Configurer la sortie d'erreur**  
 Spécifiez le mode de gestion des erreurs au niveau des lignes. Des erreurs peuvent se produire lorsque la transformation corrige des données de la source de données connectée, en raison de valeurs de données ou de contraintes de validation inattendues.  
  
 Les valeurs suivantes sont valides :  
  
-   **Composant défaillant**, qui indique que la transformation a échoué et que les données d’entrée ne sont pas insérées dans la base de données Data Quality Services. Ceci est la valeur par défaut.  
  
-   **Réacheminer la ligne**, qui indique que les données d’entrée ne sont pas insérées dans la base de données Data Quality Services et qu’elles sont redirigées vers la sortie d’erreur.  
  
##  <a name="mapping"></a> Définir les options sur l'onglet mappage  
 Pour plus d’informations sur la façon de mapper des colonnes à des domaines composites, consultez [Mapper des colonnes à des domaines composites](../../../integration-services/data-flow/transformations/map-columns-to-composite-domains.md).  
  
 **Colonnes d'entrée disponibles**  
 Répertorie les colonnes à partir de la source de données connectée. Sélectionnez une ou plusieurs colonnes qui contiennent les données que vous souhaitez corriger.  
  
 **Colonne d'entrée**  
 Répertorie une colonne d’entrée sélectionnée dans la zone **Colonnes d’entrée disponibles**.  
  
 **Domaine**  
 Sélectionnez un domaine pour la mapper à la colonne d'entrée.  
  
 **Alias source**  
 Répertorie la colonne source qui contient la valeur de colonne d'origine.  
  
 Cliquez dans le champ pour modifier le nom de colonne.  
  
 **Alias de sortie**  
 Répertorie la colonne générée par la **Transformation de nettoyage DQS**. Cette colonne contient la valeur de colonne d'origine ou la valeur corrigée.  
  
 Cliquez dans le champ pour modifier le nom de colonne.  
  
 **Alias d'état**  
 Répertorie la colonne qui contient les informations d'état des données corrigées. Cliquez dans le champ pour modifier le nom de colonne.  
  
##  <a name="advanced"></a> Définir les options de l'onglet Avancé  
 **Normaliser la sortie**  
 Indique s'il faut retourner les données dans un format standardisé en fonction du format de sortie défini pour les domaines. Pour plus d’informations sur le format standardisé, consultez [Nettoyage de données](../../../data-quality-services/data-cleansing.md).  
  
 **Confiance**  
 Indique s'il faut inclure le niveau de confiance pour les données corrigées. Le niveau de confiance indique le degré de certitude de DQS pour la correction ou la suggestion. Pour plus d’informations sur les niveaux de confiance, consultez [Nettoyage de données](../../../data-quality-services/data-cleansing.md).  
  
 **Reason**  
 Indique s'il faut inclure la raison de la correction des données.  
  
 **Données ajoutées**  
 Indique s'il faut retourner des informations supplémentaires reçues d'un fournisseur de données de référence existant. Pour plus d’informations, consultez [Reference Data Services in DQS](../../../data-quality-services/reference-data-services-in-dqs.md).  
  
 **Schéma de données ajoutées**  
 Indique s'il faut retourner le schéma de données. Pour plus d’informations, consultez [Attacher un domaine ou un domaine composite à des données de référence](../../../data-quality-services/attach-domain-or-composite-domain-to-reference-data.md).  
  
##  <a name="manager"></a> Définir les options dans la boîte de dialogue Gestionnaire de connexions du nettoyage DQS  
 **Nom du serveur**  
 Sélectionnez ou entrez le nom du serveur DQS auquel vous souhaitez vous connecter. Pour plus d’informations sur le serveur, consultez [Administration de DQS](../../../data-quality-services/dqs-administration.md).  
  
 **Tester la connexion**  
 Cliquez pour confirmer que la connexion que vous avez spécifiée fonctionne.  
  
 Vous pouvez également ouvrir la boîte de dialogue **Gestionnaire de connexions du nettoyage DQS** à partir de la zone de connexions, en procédant comme suit :  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], ouvrez un projet [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] ou créez-en un nouveau.  
  
2.  Cliquez avec le bouton droit dans la zone des connexions, cliquez sur **Nouvelle connexion**, puis cliquez sur **DQS**.  
  
3.  Cliquez sur **Ajouter**.  
  
## Voir aussi  
 [Appliquer des règles de qualité des données à la source de données](../../../integration-services/data-flow/transformations/apply-data-quality-rules-to-data-source.md)  
  
  