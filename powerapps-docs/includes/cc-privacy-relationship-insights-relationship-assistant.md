リレーションシップ アシスタント機能を有効にすると、やり取りの限定的なデータ (送信者の名前と電子メール アドレス、電子メール本文の抜粋を含む) が取得されます (ただし、[!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] には保存されません)。データを取得する目的は、電子メールについて関連性のあるインサイトを表示することです。 さらに、リレーションシップ アシスタント機能を構成して、ニュース、金融、フライト情報に関する情報を取得できます。そのために、MSN マネーや Bing ([!INCLUDE[pn_ms_dyn_365](pn-ms-dyn-365.md)] Core Services とは見なされない) などの外部コンポーネントに要求が送信されます。 管理者はリレーションシップ アシスタント機能を有効または無効にすることができます。そのためには、**設定** > **インテリジェンスの構成**に移動し、**リレーションシップ アシスタント**タブをクリックして、適切な選択を行います。  
  
 リレーションシップ アシスタント機能に関連する外部コンポーネントについては、以下のセクションで説明します。  
  
 **[!INCLUDE[pn_bing](pn-bing.md)]**  
  
 リレーションシップ アシスタントは [!INCLUDE[pn_bing](pn-bing.md)] を使用して関連性のあるニュースを検索し、ユーザーに表示します。このとき、そのユーザーの [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] データから、取引先企業名を使用します。  
  
 **[!INCLUDE[pn_ms_MSN_Money](pn-ms-msn-money.md)]**  
  
 リレーションシップ アシスタントは [!INCLUDE[pn_ms_MSN_Money](pn-ms-msn-money.md)] を使用して関連性のある株価情報をユーザーに表示します。このとき、そのユーザーの [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] データから、取引先企業の株式銘柄コードを使用します。