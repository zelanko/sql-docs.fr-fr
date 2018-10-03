---
title: Boîte de Message d’Exception de programme | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- exception message box [SQL Server]
- displaying exception message box
ms.assetid: c771985b-149c-459a-b3cb-7b15fde01150
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8cf02e2759c36ae6408beed0d72b677e130e105a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48164109"
---
# <a name="program-exception-message-box"></a>Programmer la boîte de message d'exceptions
  Vous pouvez utiliser la boîte de message d’exception dans vos applications pour fournir un contrôle nettement supérieur sur les messages que celui fourni par le <xref:System.Windows.Forms.MessageBox> classe. Pour plus d’informations, consultez [programmation de boîte de Message d’Exception](../../../2014/database-engine/dev-guide/exception-message-box-programming.md). Pour plus d’informations sur la façon d’obtenir et de déployer la .dll de boîte de message exception, consultez [déploiement d’une Application de boîte de Message d’Exception](../../../2014/database-engine/dev-guide/deploying-an-exception-message-box-application.md).  
  
## <a name="procedure"></a>Procédure  
  
#### <a name="to-handle-an-exception-by-using-the-exception-message-box"></a>Pour gérer une exception en utilisant la boîte de message d'exception  
  
1.  Ajoutez une référence dans votre projet de code managé à l'assembly Microsoft.ExceptionMessageBox.dll.  
  
2.  (Facultatif) Ajouter un `using` (c#) ou `Imports` ([!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic .NET) directive à utiliser le <xref:Microsoft.SqlServer.MessageBox> espace de noms.  
  
3.  Créez un bloc try-catch pour gérer l'exception anticipée.  
  
4.  Dans le `catch` bloquer, créez une instance de la <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> classe. Passer le <xref:System.Exception> objet géré par le `try` - `catch` bloc.  
  
5.  (Facultatif) Définissez une ou plusieurs des propriétés suivantes sur <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox>:  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Buttons%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons> énumération qui spécifie les boutons à afficher dans la boîte de message d’exception.  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.DefaultButton%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxDefaultButton> énumération qui spécifie le bouton par défaut pour la boîte de message d’exception.  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Options%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxOptions> énumération qui vous permet de contrôler d’autres comportements de la boîte de message d’exception.  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Symbol%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxSymbol> énumération qui spécifie le symbole à afficher dans la boîte de message d’exception.  
  
6.  Appelez la méthode <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Show%2A> . Passez la fenêtre parente à laquelle la boîte de message d'exception appartient.  
  
7.  (Facultatif) Notez la valeur de retourné <xref:System.Windows.Forms.DialogResult> cliqué énumération si vous devez déterminer sur quel bouton l’utilisateur.  
  
#### <a name="to-display-the-exception-message-box-without-an-exception"></a>Pour afficher la boîte de message d'exception sans exception  
  
1.  Ajoutez une référence dans votre projet de code managé à l'assembly Microsoft.ExceptionMessageBox.dll.  
  
2.  (Facultatif) Ajouter un `using` (c#) ou `Imports` directive (Visual Basic .NET) à utiliser le <xref:Microsoft.SqlServer.MessageBox> espace de noms.  
  
3.  Créez une instance de la classe <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> . Passer le texte du message en tant qu’un <xref:System.String> valeur.  
  
4.  (Facultatif) Définissez une ou plusieurs des propriétés suivantes sur <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox>:  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Buttons%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons> énumération qui spécifie les boutons à afficher dans la boîte de message d’exception.  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Caption%2A> - légende de boîte de dialogue de la boîte de message d'exception ;  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.DefaultButton%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxDefaultButton> énumération qui spécifie le bouton par défaut pour la boîte de dialogue de la boîte de message d’exception.  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Options%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxOptions> énumération qui vous permet de contrôler d’autres comportements de la boîte de message d’exception.  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Symbol%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxSymbol> énumération qui spécifie le symbole à afficher dans la boîte de message d’exception.  
  
5.  Appelez la méthode <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Show%2A> . Passez la fenêtre parente à laquelle la boîte de message d'exception appartient.  
  
6.  (Facultatif) Notez la valeur de retourné <xref:System.Windows.Forms.DialogResult> cliqué énumération si vous devez déterminer sur quel bouton l’utilisateur.  
  
#### <a name="to-display-the-exception-message-box-with-customized-buttons"></a>Pour afficher la boîte de message d'exception avec des boutons personnalisés  
  
1.  Ajoutez une référence dans votre projet de code managé à l'assembly Microsoft.ExceptionMessageBox.dll.  
  
2.  (Facultatif) Ajouter un `using` (c#) ou `Imports` directive (Visual Basic .NET) à utiliser le <xref:Microsoft.SqlServer.MessageBox> espace de noms.  
  
3.  Créez une instance de la classe <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> en appliquant l'une des deux méthodes suivantes :  
  
    -   Passer le <xref:System.Exception> objet géré par un `try` - `catch` bloc.  
  
    -   Passer le texte du message en tant qu’un <xref:System.String> valeur.  
  
4.  Définissez une de ces valeurs pour <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Buttons%2A>:  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.AbortRetryIgnore> -Affiche la **abandonner**, **de nouvelle tentative**, et **ignorer** boutons.  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.Custom> -Affiche les boutons personnalisés.  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.OK> -Affiche la **OK** bouton.  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.OKCancel> -Affiche la **OK** et **Annuler** boutons.  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.RetryCancel> -Affiche la **de nouvelle tentative** et **Annuler** boutons.  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.YesNo> -affiche **Oui** et **non** boutons.  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.YesNoCancel> -affiche **Oui**, **non**, et **Annuler** boutons.  
  
5.  (Facultatif) Si vous utilisez des boutons personnalisés, appelez une des surcharges de la <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.SetButtonText%2A> méthode pour spécifier le texte pour jusqu'à cinq boutons personnalisés.  
  
6.  Appelez la méthode <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Show%2A> . Passez la fenêtre parente à laquelle la boîte de message d'exception appartient.  
  
7.  (Facultatif) Notez la valeur de retourné <xref:System.Windows.Forms.DialogResult> cliqué énumération si vous devez déterminer sur quel bouton l’utilisateur. Si vous utilisez des boutons personnalisés, notez la valeur de <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxDialogResult> pour le <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CustomDialogResult%2A> cliqué de propriété afin de déterminer lequel des personnalisé boutons l’utilisateur.  
  
#### <a name="to-allow-users-to-decide-whether-to-show-the-exception-message-box"></a>Pour permettre aux utilisateurs de décider d'afficher ou non la boîte de message d'exception  
  
1.  Ajoutez une référence dans votre projet de code managé à l'assembly Microsoft.ExceptionMessageBox.dll.  
  
2.  (Facultatif) Ajouter un `using` (c#) ou `Imports` directive (Visual Basic .NET) à utiliser le <xref:Microsoft.SqlServer.MessageBox> espace de noms.  
  
3.  Créez une instance de la classe <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> en appliquant l'une des deux méthodes suivantes :  
  
    -   Passer le <xref:System.Exception> objet géré par un `try` - `catch` bloc.  
  
    -   Passer le texte du message en tant qu’un <xref:System.String> valeur.  
  
4.  Définir le <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.ShowCheckbox%2A> propriété `true`.  
  
5.  (Facultatif) Spécifiez le texte qui invite l’utilisateur à décider s’il faut afficher la boîte de message d’exception à nouveau pour <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CheckboxText%2A>. Le texte par défaut est "Ne plus afficher ce message".  
  
6.  Si vous devez conserver la décision de l’utilisateur uniquement pour la durée d’exécution de l’application, définissez la valeur de <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.IsCheckboxChecked%2A> global <xref:System.Boolean> variable. Évaluez cette valeur avant de créer une instance de la boîte de message d'exception.  
  
7.  Si vous devez stocker définitivement la décision d'un utilisateur, procédez comme suit :  
  
    1.  Appelez la méthode CreateSubKey pour ouvrir une clé de Registre personnalisée que votre application utilise et définissez <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CheckboxRegistryKey%2A> sur l’objet RegistryKey retourné.  
  
    2.  Attribuez à <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CheckboxRegistryValue%2A> le nom de la valeur de Registre utilisée.  
  
    3.  Définissez <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CheckboxRegistryMeansDoNotShowDialog%2A> à `true`.  
  
    4.  Appelez la méthode <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Show%2A> . La clé de Registre spécifiée est évaluée et la boîte de message d'exception est affichée uniquement si les données stockées dans la clé de Registre sont définies sur 0. Si la boîte de dialogue est affichée et que l'utilisateur active la case à cocher avant de cliquer sur un bouton, les données dans la clé de Registre sont définies sur 1.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise la boîte de message d’exception avec uniquement le **OK** bouton pour afficher des informations à partir d’une exception d’application qui inclut l’exception gérée avec des informations supplémentaires spécifiques à l’application.  
  
 [!code-csharp[HowTo#emb_showOKbutton](../../snippets/csharp/SQL15/replication/howto/cs/embform.cs#emb_showokbutton)]  
  
 [!code-vb[HowTo#emb_vb_showOKbutton](../../snippets/visualbasic/SQL15/replication/howto/vb/embform.vb#emb_vb_showokbutton)]  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise la boîte de message d’exception avec **Oui** et **non** à partir de laquelle l’utilisateur choisit les boutons.  
  
 [!code-csharp[HowTo#emb_showYesNobutton](../../snippets/csharp/SQL15/replication/howto/cs/embform.cs#emb_showyesnobutton)]  
  
 [!code-vb[HowTo#emb_vb_showYesNobutton](../../snippets/visualbasic/SQL15/replication/howto/vb/embform.vb#emb_vb_showyesnobutton)]  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise la boîte de message d'exception avec des boutons personnalisés.  
  
 [!code-csharp[HowTo#emb_showcustombutton](../../snippets/csharp/SQL15/replication/howto/cs/embform.cs#emb_showcustombutton)]  
  
 [!code-vb[HowTo#emb_vb_showcustombutton](../../snippets/visualbasic/SQL15/replication/howto/vb/embform.vb#emb_vb_showcustombutton)]  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise la case à cocher pour déterminer s'il faut afficher la boîte de message d'exception.  
  
 [!code-csharp[HowTo#emb_usecheckbox](../../snippets/csharp/SQL15/replication/howto/cs/embform.cs#emb_usecheckbox)]  
  
 [!code-vb[HowTo#emb_vb_usecheckbox](../../snippets/visualbasic/SQL15/replication/howto/vb/embform.vb#emb_vb_usecheckbox)]  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise la case à cocher et une clé du Registre pour déterminer s'il faut afficher la boîte de message d'exception.  
  
 [!code-csharp[HowTo#emb_useregkey](../../snippets/csharp/SQL15/replication/howto/cs/embform.cs#emb_useregkey)]  
  
 [!code-vb[HowTo#emb_vb_useregkey](../../snippets/visualbasic/SQL15/replication/howto/vb/embform.vb#emb_vb_useregkey)]  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise la boîte de message d'exception pour afficher des informations supplémentaires utiles lors d'un dépannage ou d'un débogage.  
  
 [!code-csharp[HowTo#emb_moreinfo](../../snippets/csharp/SQL15/replication/howto/cs/embform.cs#emb_moreinfo)]  
  
 [!code-vb[HowTo#emb_vb_moreinfo](../../snippets/visualbasic/SQL15/replication/howto/vb/embform.vb#emb_vb_moreinfo)]  
  
  
