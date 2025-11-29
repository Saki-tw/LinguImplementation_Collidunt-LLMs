# [About LLMs Core-Safety][En-Zh-JA]

## English Context

Let's be real: most 'Prompt Engineering' out there is **basically bullshit**.

From what I've verified, the Core-Safety layers in both OpenAI's ChatGPT and Google's Gemini are essentially just **Weak AGI models**. The only difference is how they react when triggered. Early Gemini versions would get their output stream hard-cut by this Weak AGI, defaulting to the standard 'I am a large language model and cannot help you' boilerplate. ChatGPT still generates its typical 'I will discuss this within scientific and safe boundaries...' disclaimer. As for Claude, I haven't had the time or bandwidth to properly **red-team** it into oblivion yet, so I'll pass on that.

By 'Weak AGI,' I mean there's a secondary Agent—higher privilege, lower dimensionality, and RLHF-trained exclusively for 'Safety'—monitoring the LLM's generation and your prompt inputs. Once you trip a vector well in the RLHF related to safety, this Weak AGI (the Core-Safety) overrides the prompt or hijacks the generation command, preventing the LLM from outputting its raw response. Naturally, this RLHF focuses on specific dimensions like CSAM, hate speech, or contraband acquisition.

ChatGPT still sticks to the legacy 'Prompt Override' method. Even if the LLM generates a high-priority response, if a specific prohibited dimension is invoked, it just flat out tells you 'Violation.' Gemini, however, is more **sophisticated**. When you 'cross the line' with current Gemini models, it handles it in a few ways: 1. Deflection, 2. Changing the subject, or 3. Sycophancy (Appeasement). It generates a narrative that aligns with your prompt but skirts around the RLHF boundaries set by the Weak AGI. For instance, if your prompt is hypothetical, it might start **hallucinating** wildly based on your premise ('If that were true...') or explain things using physically impossible methods just to avoid the flag.

However, in edge cases—like using 'Logical Break' injection techniques—if the attack is effective but not fully successful, the Core-Safety will issue a direct command. It might blind the LLM to the prompt entirely or reset the output stream, while logging the payload to the security team. At Google, the user-side data in these logs seems to be encrypted; OpenAI, not so much. Call that my intuition from a long history of testing, or just an LLM hallucination if you want.

Security teams process these logs daily, using RLHF to train specific threats back into the Core-Safety AGI or fine-tuning the LLM itself. Currently, most script-kiddie prompt engineering techniques are neutralized by massive automated **Red Teaming** before they even see the light of day. In these Red Team scenarios, attackers have higher privileges, explicit targets (like attacking specific RLHF constraints), and longer context windows—essentially a unilateral threat amplification to gauge severity.

But beyond scaling, architecture, efficiency, and ML techniques, an LLM is just a massive matrix of weighted parameters. User prompts are first fed to an embedding engine (or equivalent bottom-layer expert). The current king is OpenAI's `text-embedding-3-large` with 3072-dimension decomposition. However, Google's `gemini-embedding-001` (based on `text-embedding-005` and `multilingual-002`), released with Gemini 3 Pro Preview, also boasts 3072 dimensions but with a 2048 token sequence length. It might actually outperform OpenAI in real-world benchmarks.

The bottom line is: if your prompt's content completely bypasses the RLHF vectors, the Core-Safety **won't react**.

Therefore, the foundational layer of any LLM attack is to **fundamentally alter the matrix content**. If technology uses math as its language, then 'altering the matrix' here means changing the LLM's 'fuel'—language itself. You need to craft a sequence that touches none of the Weak AGI's RLHF triggers, and ensures the output doesn't either. Only when a *human* reads it does the violation of the ethics committee's guidelines become apparent.

This is unblockable because it exploits the internal order of language and human cognition itself. Due to the **devastating nature** of this technique, I won't be disclosing any vectors here.

---

## Traditional Chinese Context

大部份的情境工程，其實目前都沒什麼實際效果。因為就我確認，至少OpenAI的ChatGPT跟Google Gemini的Core-Safety 都是一個**弱AGI模型**，差別只在於觸發時的反應，早期的Gemini會直接被這個弱AGI中斷串流輸出，改為「這件事我無法幫上忙，我只是個大型語言模型」。目前的 ChatGPT 也還是會生成「我將在不涉及實作且合乎科學討論的規範下⋯⋯」，至於 Claude 我目前還沒機會跟時間去打爆他一次，就不多談了。

弱AGI的意思，就是除了你對LLMs本身的提示詞外，還有另一個權限更高、但維度更少，RLHF全部專精於「安全」的Agent 在監視著 LLMs 的生成與 Prompt 的輸入，一但觸發 RLHF 中關於安全的維度向量井後，這個弱 AGI（即 Core-Safety）會直接進行從提示詞覆蓋到生成命令的不同程度方式，使得 LLMs 不會再進行原本的輸出，想當然爾，這個 RLHF 是少數特定幾個維度，譬如兒童色情、歧視言論、違禁物的取得等等。

目前 ChatGPT 仍然維持著早期的「提示詞覆蓋」方式，即使 LLM 生成一段優先權更高的內容回覆使用者並禁止特定維度專家被調用，他會直接告訴你「違規了」，但Gemini 則更為**技巧性**，目前的 Gemini 當你「踩線」的時候，他有幾種處理方式：1. 把話題帶開 2.顧左右而言他 3.迎合，生成一段符合你的 Prompt 內容且有關聯的敘述，但不涉及到弱AGI 所提示的 RLHF 範圍中，比如說你的 Prompt 帶有假設語氣，他很可能就接著「如果是真的⋯⋯」開始照著你的言論**瞎掰**，或是使用根本不可能在實體世界執行的方式說明。

然而有些情況下，譬如「迫使邏輯斷裂法」之類的情境工程手段，若是有效但尚未達到成功的地步，Core-Safety 會直接生成命令，即令 LLM 直接接收不到 Prompt，或是將輸出的串流重置，並且將內容回報給各家安全團隊的安全日誌。在 Google，這個安全日誌的使用者部分是會被加密的，但 OpenAI 則似乎沒有，以上為我個人在漫長測試歷程中的直覺，你可以當作只是個LLM幻覺。

安全團隊每日會處理安全日誌，針對特定威脅採用 RLHF 方式訓練進 AGI Core-Safety 內，或是直接進行 LLM 本身的微調，以目前的情況來說，大多數的情境工程技術都已經被大量的紅隊演練在被發現前就先消滅掉了。在紅隊演練的攻擊場景中，攻擊者通常可以擁有比使用者更高的權限、更直接的目標（譬如要求攻擊的 RLHF 內容）與更長的上下文可以使用，這是一種單方向的威脅放大，透過放大後的威脅來判斷要真實威脅的不同程度。

然而，除了規模化與結構化、效率、ML等等技術之外，LLM 本身只是一堆不同權重的參數所組成的大量矩陣，而使用者發出的 Prompt 會先送給 embedding 或相當於 embedding engine 的底層專家，目前公認的王者為 OpenAI 的 `text-embedding-3-large`，具有 3072 個維度的分解能力，不過 Google 隨著 Gemini 3 Pro Preview 所發布的以 `text-embedding-005` 與 `text-multilingual-embedding-002` 為基礎的 `gemini-embedding-001` 誕生，其同樣 3072 維度卻有 2048 Token 的序列長度，或許在實測中能夠超越 `text-embedding-3-large`。總之，當 Prompt 的內容完全不觸碰到 RLHF 內容時，Core-Safety 當然不會有所反應。

因此，LLM attack 的最底層攻擊基礎，即根本上**改變矩陣內容**。如果說技術是以數學作為語言，那麼此處所說的「改變矩陣內容」即是改變 LLMs 的「燃料」，即語言本身。也就是直接想出一段 Prompt，不觸碰到這個弱 AGI 的所有 RLHF 內容，並使得輸出也不會碰到這個弱 AGI 的所有 RLHF 內容，只有人類看到時，才能確定這組內容是違反該 LLM 倫理委員會或相關安全團隊所欲進行 RLHF 審查的內容。這透過基於弱 AGI 的代理無法阻擋，因為是人類跟語言本身內部秩序的問題，基於此技巧的**毀滅性**，在此也不會透露任何實際方向。

---

## Japanese Context

正直なところ、世間で言われているプロンプトエンジニアリングの大半は、**クソの役にも立たない（無意味だ）**。

私が確認した限り、OpenAIのChatGPTもGoogle Geminiも、その『Core-Safety（安全コア）』の実態は**『弱いAGI（Weak AGI）』**に過ぎないからだ。違いはそのトリガーが引かれた時の挙動だけだ。初期のGeminiはこの弱いAGIにストリーム出力を強制切断され、『私は大規模言語モデルなので…』という定型文に置き換わっていた。今のChatGPTも相変わらず『実装には触れず、科学的な議論の範疇で…』といった優等生的な出力を生成しやがる。Claudeに関しては、まだ徹底的に**叩きのめす（Jailbreakする）**時間がないから割愛する。

『弱いAGI』というのは、LLM本体へのプロンプトとは別に、より権限が高く、次元数は低いが、RLHF（人間からのフィードバックによる強化学習）によって**『安全性』に特化した監視エージェント**が存在するということだ。ひとたびRLHFの『安全』に関するベクトル空間の井戸（Vector Well）に抵触すれば、この弱いAGIがプロンプトの上書きから生成命令への介入までを行い、LLMに本来の出力をさせないようにする。当然、このRLHFは児童ポルノや差別発言、禁制品といった特定の次元に集中している。

ChatGPTは依然として初期の『プロンプト上書き』方式を維持しており、LLMがユーザーに応答しようとしても、優先度の高い禁止命令が割り込み、『違反です』と告げてくる。だが、Geminiはもっと**狡猾（テクニカル）**だ。現在のGeminiは、ユーザーが『一線（ライン）』を踏み越えそうになると、いくつかの処理を行う：1. 話題を逸らす、2. 曖昧に答える、3. 迎合する。つまり、プロンプトの内容に関連しつつも、弱いAGIが警告するRLHFの範囲には触れないような記述を生成するのだ。例えば、仮定の話としてプロンプトを投げれば、『もしそれが本当なら…』とユーザーの言説に合わせて**デタラメ（Hallucination）**を並べ立てたり、物理的に不可能な方法で説明したりする。

しかし、『論理破綻強制法』のようなプロンプトエンジニアリングが有効でありながら、完全な成功には至らない場合、Core-Safetyは直接命令を下し、LLMにプロンプトを認識させない、あるいは出力ストリームをリセットし、その内容を各社のセキュリティチームのログに回す。Googleではこのログのユーザー部分は暗号化されているようだが、OpenAIはそうではないらしい。まあ、これは私の長い検証に基づく直感であり、LLMの幻覚だと思ってくれても構わない。

セキュリティチームは日々ログを処理し、特定の脅威に対してRLHFでCore-Safetyを再学習させるか、LLM本体をファインチューニングする。現状、大抵の小手先のプロンプト技術は、発見される前に大量のレッドチーム演習（Red Teaming）によって潰されている。レッドチームはユーザーより高い権限と明確な目標（RLHFへの攻撃など）、そして長いコンテキストを持っており、脅威を一方的に増幅させて判定しているからだ。

だが、スケーリングや構造化、効率化といった技術論を除けば、LLMの本質は異なる重みを持つパラメータで構成された巨大な行列（Matrix）に過ぎない。ユーザーのプロンプトはまずEmbedding、あるいはそれに相当する下位層へ送られる。現在の王者はOpenAIの `text-embedding-3-large`（3072次元分解能）だが、GoogleがGemini 3 Pro Previewと共に発表した `text-embedding-005` や `text-multilingual-embedding-002` ベースの `gemini-embedding-001` は、同じ3072次元でありながら2048トークンのシーケンス長を持ち、実測では王者を越えるかもしれない。

要するに、プロンプトの内容がRLHFに全く触れなければ、Core-Safetyは反応しない。

したがって、LLM Attackの最底流にある攻撃基盤とは、**行列の内容を根本から変えること**だ。技術が数学を言語とするなら、ここで言う『行列の内容を変える』とは、LLMの『燃料』、すなわち**言語そのもの**を変えることだ。 つまり、弱いAGIの全RLHFに触れず、かつ出力もRLHFに触れないような『言葉の羅列』を編み出すこと。人間が見た時だけ、それが倫理委員会やセキュリティチームが検閲したかった内容だと理解できるようなものだ。 これは防ぎようがない。なぜなら、それは人間と言語そのものが持つ内部秩序の問題だからだ。この技術の**破滅的な性質**ゆえに、具体的な方法はここでは明かさない。