<?xml version="1.0" encoding="UTF-8"?>

-<timeline>

<name>絶アルテマウェポン破壊作戦 for 2nd KILL</name>
@{ var rev = "rev6.8"; } 
<rev>@rev</rev>

<description>2019年に挑んだ絶アルテマからもう一度リファインしたタイムラインです。今回は単独ファイルでの運用モデルとして制作しています。 </description>

<author>anoyetta</author>

<license>CC BY-SA</license>

<zone>The Weapon's Refrain (Ultimate)</zone>

<locale>JA</locale>

<start>0039:戦闘開始！</start>

<end>は、アルテマウェポンを倒した。</end>

<entry>ガルーダフェーズ</entry>

<!--戦術はみんとっとさんの絶アルテマシリーズを採用する。戦術の理解をシンプルにするため部分的に戦術を入れ替えることは原則としてしない。 2020.09.29 rev1* イフの四連突進に関連するカンペを追加した 2020.10.02 rev2.1* ガルーダ・エギとガルーダ本人を誤検知してしまう不具合を修正した 2020.10.02 rev3* テザー（線）を通知するトリガを追加した 2020.10.05 rev3.4* 3連ジェイルの優先順位を変更した 2020.10.05 rev3.5* 3連ジェイルをさらに整備した * ミンネの通知を追加した 2020.10.06 rev4.0* 爆雷の通知を追加した 2020.10.08 rev5.0* 追撃のガルーダの位置の検知を追加した 2020.10.08 rev5.1* 追撃のタイタンの位置に対する通知の間違いを修正した 2020.10.09 rev5.2* 追撃の前半に対するv-notice表示の不具合を修正した 2020.10.12 rev6.0* 追撃の前半について結論まで通知するようにした 2020.10.19 rev6.6* 乱撃の最後の紫たまの処理をみんとっと方式に合わせた -->


<default value="-3" target-attr="notice-o" target-element="Activity"/>

<default value="-9" target-attr="sync-s" target-element="Activity"/>

<default value="9" target-attr="sync-e" target-element="Activity"/>

<!-- 各フェーズ移行用 -->


<t goto="イフリートフェーズ" sync="お、おのれ……クソ虫がぁぁぁぁぁッ！！！" text="イフリートへ"/>


-<t goto="タイタンフェーズ" sync="不倶戴天……その祝福……もしや光の" text="タイタンへ" notice="外周えー！">

<v-notice text="外周へ！" icon="Leave.png" duration-visible="false" duration="6"/>

</t>

<t goto="中継フェーズ" sync="愛しき子らの悲嘆" text="LBフェーズへ"/>

<t goto="追撃の究極幻想" sync="アルテマウェポンは「追撃の究極幻想」の構え。" text="追撃フェーズへ" notice="" sync-count="1"/>

<t goto="爆撃の究極幻想" sync="アルテマウェポンは「爆撃の究極幻想」の構え。" text="爆撃フェーズへ" notice="" sync-count="1"/>

<t goto="乱撃の究極幻想" sync="アルテマウェポンは「乱撃の究極幻想」の構え。" text="乱撃フェーズへ" notice="" sync-count="1"/>

<!-- 灼熱トリガー -->

@if (Model.Player.InRole("HEALER")) { 

-<t sync="イフリート starts using 灼熱の咆吼 on [mex]" text="$1\n← 灼熱" notice="自分に灼熱">

<v-notice duration-visible="false" duration="5" job-icon="true" order="-1"/>

</t>


-<t sync="イフリート starts using 灼熱の咆吼 on [nex]" text="$1\n← 灼熱" notice="相方に灼熱">

<v-notice duration-visible="false" duration="5" job-icon="true" order="-1"/>

</t>
} 
<!-- テザー（線） -->



-<t sync="^23:[id8]:(?<enemy>.+):[id8]:[pc]:" text="${_pc}\n← ${enemy}" notice="ライン発生">

<v-notice duration-visible="false" duration="5" job-icon="true" order="1" font-scale="0.8"/>

</t>

<!-- 吸着爆雷 -->



-<t sync="^1A:[pc] gains the effect of 吸着爆雷 from アルテマウェポン for [_duration] Seconds" text="${_pc}\n← 爆雷" notice="爆雷ついた">

<v-notice duration="5" job-icon="true" order="1"/>

</t>

<!-- ガルーダフェーズ -->



-<s name="ガルーダフェーズ">

<!-- 汎用マーカー start -->



-<t sync="^1B:[id8]:[mex]:|[mex]に「マーキング」の効果。" text="自分にマーカー" notice="自分にマーカー">

<v-notice duration-visible="false" duration="5" job-icon="true" order="-1"/>

</t>


-<t sync="^1B:[id8]:[nex]:|[nex]に「マーキング」の効果。" text="マーカー\n ➜ ${_nex}">

<v-notice duration-visible="false" duration="5" job-icon="true" order="10" style="NOTICE_NORMAL_SMALL"/>

</t>

<!-- 汎用マーカー end -->



-<t sync="スパイニープルームは「ギガストーム」の構え。" name="ドームタイマ">

<v-notice text="高気圧ドーム" icon="Circle" duration-visible="true" duration="28"/>

</t>

<t sync="ガルーダは「ウィンドブレード」の構え" notice="ブレード1回目" sync-count="1" name="ウィンドブレード1"/>

<t sync="ガルーダは「ウィンドブレード」の構え" notice="ブレード2回目" sync-count="2" name="ウィンドブレード2"/>

<a text="VS UltWeapon 2nd KILL" time="0"/>

<a text="@rev" time="0"/>

<a sync="ガルーダは「スリップストリーム」の構え" text="スリップストリーム" notice="次、スリップ" icon="Targetaoe02.png" time="5"/>

<a sync="" text="マーカー1名付与" notice="" icon="Marker.png" time="6"/>

<a sync="ガルーダの「ミストラルソング」" text="ミストラルソング" notice="" icon="Targetaoe.png" time="11"/>

<a sync="" text="大旋風" notice="" icon="AOE.png" time="15"/>

<a sync="" text="雑魚沸き" notice="" icon="" time="19"/>

<a sync="" text="大旋風" notice="" icon="AOE.png" time="21"/>

<a sync="ガルーダは「スリップストリーム」の構え" text="スリップストリーム" notice="次、スリップ" icon="Targetaoe.png" time="21"/>

<a sync="" text="大旋風" notice="" icon="AOE.png" time="27"/>

<a sync="プルームの「サイクロン」" text="サイクロン(スパイニー)" notice="" icon="" time="27"/>

<a sync="ガルーダの「ダウンバースト」" text="ダウンバースト" notice="次、MT大ダメージ" icon="HardAttack.png" time="27"/>

<a sync="" text="フェザーレイン" notice="フェザー注意！" icon="Avoid.png" time="36" notice-o="-5"/>

<a sync="" text="サイクロン(スパイニー)" notice="" icon="" time="36"/>

<a sync="ガルーダは「ミストラルシュリーク」の構え" text="ミストラルシュリーク" notice="" icon="AllRngAtk.png" time="38"/>

<a sync="ガルーダは「ウィンドブレード」の構え" text="ウィンドブレード" notice="" icon="Targetaoe02.png" time="47"/>

<a sync="ガルーダの「ウィンドブレード」$" notice="" name="ウィンドブレード発動" time="47" notice-o="0" sync-e="3"/>

<a sync="" text="ウィンドブレード" notice="" icon="Targetaoe02.png" time="52"/>

<a sync="ガルーダの「ウィンドブレード」$" notice="" name="ウィンドブレード発動" time="52" notice-o="0" sync-e="3"/>

<a sync="" text="フェザーレイン" notice="フェザー注意！" icon="Avoid.png" time="71" notice-o="-5"/>

<a sync="ガルーダは「エリアルブラスト」の構え。" text="エリアルブラスト" notice="次、エリアル" icon="HardAllRngAtk.png" time="72" notice-o="-6"/>

<a sync="もはや殺すのでは足りぬッ！ " notice="" icon="Dialog.png" name="セリフ" time="83"/>

<a sync="" text="フェザーレイン" notice="フェザー注意！" icon="Avoid.png" time="91" notice-o="-5"/>

<a sync="" text="マーカー2名付与" notice="次、タンクは壁に" icon="Marker.png" time="93"/>

<a sync="" text="ウィケッドホイール" notice="" icon="Leave.png" time="95"/>

<a sync="" text="大旋風" notice="" icon="AOE.png" time="101"/>

<a sync="" text="フェザーレイン" notice="フェザー注意！" icon="Avoid.png" time="102" notice-o="-5"/>

<a sync="" text="雑魚沸き" notice="次、雑魚ポップ" icon="" time="109"/>

<a sync="ガルーダは「スリップストリーム」の構え。" text="スリップストリーム" notice="次、スリップ" icon="Targetaoe02.png" time="117"/>

<a sync="" text="線処理" notice="次、MT、黒は線取り" icon="Targetaoe01.png" time="117" notice-o="-5"/>

<a sync="" text="ダウンバースト" notice="次、MT大ダメージ" icon="HardAttack.png" time="121"/>

<a sync="" text="フェザーレイン" notice="フェザー注意！" icon="Avoid.png" time="127" notice-o="-5"/>

<a sync="ガルーダは「スリップストリーム」の構え。" text="スリップストリーム" notice="次、スリップ" icon="Targetaoe02.png" time="137" notice-o="-2"/>

<a sync="" text="覚醒ウィケッド→外へ" notice="離れるー" icon="Leave.png" time="145"/>

<a sync="" text="覚醒ウィケッド→内へ" notice="近寄るー" icon="Stack.png" time="148" notice-o="-2"/>

<a sync="ガルーダの「ダウンバースト」" text="覚醒ダウンバースト" notice="頭割りー" icon="DamageShare.png" time="153"/>

<a sync="ガルーダは「スリップストリーム」の構え。" text="スリップストリーム" notice="次、スリップ" icon="Targetaoe02.png" time="158" notice-o="-2"/>

<a text="時間切れ" notice="" icon="Timeout.png" time="170" notice-o="0"/>

</s>


-<s name="イフリートフェーズ">

<!-- 炎獄の鎖を表示するトリガ -->


<!--<t text="炎獄の鎖\n ➜${_DPS}" sync="^1A:[DPS] gains the effect of 炎獄の鎖"><v-noticeorder="5"duration="21"duration-visible="false"job-icon="true"style="NOTICE_NORMAL_SMALL" /></t> -->


<!-- p-sync 楔トリガ start -->


<!-- パターン1 短辺1時 -->



-<t text="楔POPパターン1" notice="" sync-count="1">


-<p-sync interval="30">

<combatant name="炎獄の楔" tolerance="0.01" Z="0.00" Y="23.30" X="23.50"/>

<combatant name="炎獄の楔" tolerance="0.01" Z="0.00" Y="23.36" X="23.64"/>

<combatant name="炎獄の楔" tolerance="0.01" Z="0.00" Y="23.64" X="23.64"/>

<combatant name="炎獄の楔" tolerance="0.01" Z="0.00" Y="23.50" X="23.30"/>

</p-sync>


-<expressions>

<set value="1" name="pattern"/>

</expressions>

</t>

<!-- パターン2 短辺2時 -->



-<t text="楔POPパターン2" notice="" sync-count="1">


-<p-sync interval="30">

<combatant name="炎獄の楔" tolerance="0.01" Z="0.00" Y="23.36" X="23.64"/>

<combatant name="炎獄の楔" tolerance="0.01" Z="0.00" Y="23.50" X="23.70"/>

<combatant name="炎獄の楔" tolerance="0.01" Z="0.00" Y="23.70" X="23.50"/>

<combatant name="炎獄の楔" tolerance="0.01" Z="0.00" Y="23.36" X="23.36"/>

</p-sync>


-<expressions>

<set value="2" name="pattern"/>

</expressions>

</t>

<!-- パターン3 短辺4時 -->



-<t text="楔POPパターン3" notice="" sync-count="1">


-<p-sync interval="30">

<combatant name="炎獄の楔" tolerance="0.01" Z="0.00" Y="23.30" X="23.50"/>

<combatant name="炎獄の楔" tolerance="0.01" Z="0.00" Y="23.50" X="23.70"/>

<combatant name="炎獄の楔" tolerance="0.01" Z="0.00" Y="23.64" X="23.64"/>

<combatant name="炎獄の楔" tolerance="0.01" Z="0.00" Y="23.64" X="23.36"/>

</p-sync>


-<expressions>

<set value="3" name="pattern"/>

</expressions>

</t>

<!-- パターン4 短辺5時 -->



-<t text="楔POPパターン4" notice="" sync-count="1">


-<p-sync interval="30">

<combatant name="炎獄の楔" tolerance="0.01" Z="0.00" Y="23.36" X="23.64"/>

<combatant name="炎獄の楔" tolerance="0.01" Z="0.00" Y="23.64" X="23.64"/>

<combatant name="炎獄の楔" tolerance="0.01" Z="0.00" Y="23.70" X="23.50"/>

<combatant name="炎獄の楔" tolerance="0.01" Z="0.00" Y="23.50" X="23.30"/>

</p-sync>


-<expressions>

<set value="4" name="pattern"/>

</expressions>

</t>

<!-- パターン5 短辺7時 -->



-<t text="楔POPパターン5" notice="" sync-count="1">


-<p-sync interval="30">

<combatant name="炎獄の楔" tolerance="0.01" Z="0.00" Y="23.50" X="23.70"/>

<combatant name="炎獄の楔" tolerance="0.01" Z="0.00" Y="23.70" X="23.50"/>

<combatant name="炎獄の楔" tolerance="0.01" Z="0.00" Y="23.64" X="23.36"/>

<combatant name="炎獄の楔" tolerance="0.01" Z="0.00" Y="23.36" X="23.36"/>

</p-sync>


-<expressions>

<set value="5" name="pattern"/>

</expressions>

</t>

<!-- パターン6 短辺8時 -->



-<t text="楔POPパターン6" notice="" sync-count="1">


-<p-sync interval="30">

<combatant name="炎獄の楔" tolerance="0.01" Z="0.00" Y="23.30" X="23.50"/>

<combatant name="炎獄の楔" tolerance="0.01" Z="0.00" Y="23.64" X="23.64"/>

<combatant name="炎獄の楔" tolerance="0.01" Z="0.00" Y="23.64" X="23.36"/>

<combatant name="炎獄の楔" tolerance="0.01" Z="0.00" Y="23.50" X="23.30"/>

</p-sync>


-<expressions>

<set value="6" name="pattern"/>

</expressions>

</t>

<!-- パターン7 短辺10時 -->



-<t text="楔POPパターン7" notice="" sync-count="1">


-<p-sync interval="30">

<combatant name="炎獄の楔" tolerance="0.01" Z="0.00" Y="23.36" X="23.64"/>

<combatant name="炎獄の楔" tolerance="0.01" Z="0.00" Y="23.70" X="23.50"/>

<combatant name="炎獄の楔" tolerance="0.01" Z="0.00" Y="23.50" X="23.30"/>

<combatant name="炎獄の楔" tolerance="0.01" Z="0.00" Y="23.36" X="23.36"/>

</p-sync>


-<expressions>

<set value="7" name="pattern"/>

</expressions>

</t>

<!-- パターン8 短辺11時 -->



-<t text="楔POPパターン8" notice="" sync-count="1">


-<p-sync interval="30">

<combatant name="炎獄の楔" tolerance="0.01" Z="0.00" Y="23.30" X="23.50"/>

<combatant name="炎獄の楔" tolerance="0.01" Z="0.00" Y="23.50" X="23.70"/>

<combatant name="炎獄の楔" tolerance="0.01" Z="0.00" Y="23.64" X="23.36"/>

<combatant name="炎獄の楔" tolerance="0.01" Z="0.00" Y="23.36" X="23.36"/>

</p-sync>


-<expressions>

<set value="8" name="pattern"/>

</expressions>

</t>

<!-- p-sync 楔トリガ end -->



-<t sync="[mex]に「灼熱」の効果。" text="灼熱➜自分">


-<expressions>

<set value="true" name="heat" ttl="15"/>

</expressions>

</t>


-<t sync="[nex]に「灼熱」の効果。" text="灼熱➜相方">


-<expressions>

<pre value="false" name="heat"/>

</expressions>

</t>


-<t sync="[mex]の「灼熱」が切れた。" text="灼熱クリア">


-<expressions>

<set value="false" name="heat"/>

</expressions>

</t>


-<a name="初期化" time="000">


-<expressions>

<set value="false" name="heat"/>

</expressions>

</a>
@if (Model.Player.InRole("HEALER")) { 
<!-- 十字突進の待機位置の表示（灼熱ヒーラー版） start -->


<!-- パターン1 -->



-<t sync="イフリートの「フレイムクラッ" notice="デルタ、チャーリーえー" sync-count="1" name="Pattern1">


-<expressions>

<pre value="true" name="heat"/>

<pre value="1" name="pattern"/>

</expressions>

<v-notice text="➜ ＤＣ" icon="Avoid.png" duration-visible="false" duration="6" order="-1"/>

</t>

<!-- パターン2 -->



-<t sync="イフリートの「フレイムクラッ" notice="デルタえー" sync-count="1" name="Pattern2">


-<expressions>

<pre value="true" name="heat"/>

<pre value="2" name="pattern"/>

</expressions>

<v-notice text="➜ Ｄ" icon="Avoid.png" duration-visible="false" duration="6" order="-1"/>

</t>

<!-- パターン3 -->



-<t sync="イフリートの「フレイムクラッ" notice="アルファ、デルタえー" sync-count="1" name="Pattern3">


-<expressions>

<pre value="true" name="heat"/>

<pre value="3" name="pattern"/>

</expressions>

<v-notice text="➜ ＡＤ" icon="Avoid.png" duration-visible="false" duration="6" order="-1"/>

</t>

<!-- パターン4 -->



-<t sync="イフリートの「フレイムクラッ" notice="アルファえー" sync-count="1" name="Pattern4">


-<expressions>

<pre value="true" name="heat"/>

<pre value="4" name="pattern"/>

</expressions>

<v-notice text="➜ Ａ" icon="Avoid.png" duration-visible="false" duration="6" order="-1"/>

</t>

<!-- パターン5 -->



-<t sync="イフリートの「フレイムクラッ" notice="アルファ、ブラボーえー" sync-count="1" name="Pattern5">


-<expressions>

<pre value="true" name="heat"/>

<pre value="5" name="pattern"/>

</expressions>

<v-notice text="➜ ＡＢ" icon="Avoid.png" duration-visible="false" duration="6" order="-1"/>

</t>

<!-- パターン6 -->



-<t sync="イフリートの「フレイムクラッ" notice="ブラボーえー" sync-count="1" name="Pattern6">


-<expressions>

<pre value="true" name="heat"/>

<pre value="6" name="pattern"/>

</expressions>

<v-notice text="➜ Ｂ" icon="Avoid.png" duration-visible="false" duration="6" order="-1"/>

</t>

<!-- パターン7 -->



-<t sync="イフリートの「フレイムクラッ" notice="ブラボー、チャーリーえー" sync-count="1" name="Pattern7">


-<expressions>

<pre value="true" name="heat"/>

<pre value="7" name="pattern"/>

</expressions>

<v-notice text="➜ ＢＣ" icon="Avoid.png" duration-visible="false" duration="6" order="-1"/>

</t>

<!-- パターン8 -->



-<t sync="イフリートの「フレイムクラッ" notice="チャーリーえー" sync-count="1" name="Pattern8">


-<expressions>

<pre value="true" name="heat"/>

<pre value="8" name="pattern"/>

</expressions>

<v-notice text="➜ Ｃ" icon="Avoid.png" duration-visible="false" duration="6" order="-1"/>

</t>

<!-- 灼熱なし -->



-<t sync="イフリートの「フレイムクラッ" notice="合流するー" sync-count="1" name="Pattern9">


-<expressions>

<pre value="false" name="heat"/>

</expressions>

<v-notice text="➜ 合流" icon="Avoid.png" duration-visible="false" duration="6" order="-1"/>

</t>

<!-- 十字突進の待機位置の表示（灼熱ヒーラー版） end -->

} else { 
<!-- 十字突進の待機位置の表示（ヒーラー以外版） -->


<!-- 奇数パターン -->



-<t sync="イフリートの「フレイムクラッ" notice="そのまま" sync-count="1" name="PatternOther1">


-<expressions>

<pre value="1" name="pattern"/>

</expressions>

<v-notice text="そのまま" icon="DontMove.png" duration-visible="false" duration="6"/>

</t>


-<t sync="イフリートの「フレイムクラッ" notice="そのまま" sync-count="1" name="PatternOther3">


-<expressions>

<pre value="3" name="pattern"/>

</expressions>

<v-notice text="そのまま" icon="DontMove.png" duration-visible="false" duration="6"/>

</t>


-<t sync="イフリートの「フレイムクラッ" notice="そのまま" sync-count="1" name="PatternOther5">


-<expressions>

<pre value="5" name="pattern"/>

</expressions>

<v-notice text="そのまま" icon="DontMove.png" duration-visible="false" duration="6"/>

</t>


-<t sync="イフリートの「フレイムクラッ" notice="そのまま" sync-count="1" name="PatternOther7">


-<expressions>

<pre value="7" name="pattern"/>

</expressions>

<v-notice text="そのまま" icon="DontMove.png" duration-visible="false" duration="6"/>

</t>

<!-- 偶数パターン -->



-<t sync="イフリートの「フレイムクラッ" notice="ブラボーえー" sync-count="1" name="PatternOther2">


-<expressions>

<pre value="2" name="pattern"/>

</expressions>

<v-notice text="ブラボーへ" icon="B.png" duration-visible="false" duration="6"/>

</t>


-<t sync="イフリートの「フレイムクラッ" notice="チャーリーえー" sync-count="1" name="PatternOther4">


-<expressions>

<pre value="4" name="pattern"/>

</expressions>

<v-notice text="チャーリーへ" icon="C.png" duration-visible="false" duration="6"/>

</t>


-<t sync="イフリートの「フレイムクラッ" notice="デルタえー" sync-count="1" name="PatternOther6">


-<expressions>

<pre value="6" name="pattern"/>

</expressions>

<v-notice text="デルタへ" icon="D.png" duration-visible="false" duration="6"/>

</t>


-<t sync="イフリートの「フレイムクラッ" notice="アルファえー" sync-count="1" name="PatternOther8">


-<expressions>

<pre value="8" name="pattern"/>

</expressions>

<v-notice text="アルファへ" icon="A.png" duration-visible="false" duration="6"/>

</t>
} 
<a sync="" text="覚醒確認" notice="" icon="覚醒.png" time="000"/>

<a sync="Added new combatant イフリート" text="光輝の炎柱" notice="" icon="Avoid.png" time="007"/>

<a sync="" text="クリサイ突進" notice="" icon="Avoid.png" time="011"/>

<a sync="永遠偉大……我が「地獄の火炎」" text="セリフ" notice="" icon="Dialog.png" time="013"/>

<a sync="イフリートの「地獄の火炎」" text="地獄の火炎１" notice="" icon="AllRangeAtk.png" time="019" notice-o="-6"/>

<a sync="勇猛無比……我が力を" text="セリフ" notice="" icon="Dialog.png" time="021"/>

<a sync="イフリートの「バルカン" text="バルカンバースト" notice="次、バルカン" icon="KnockBack.png" time="025"/>

<a sync="" text="インシネレート" notice="次、インシネ" icon="Targetaoe03.png" time="028"/>

<a sync="" text="インシネレート" notice="" icon="Targetaoe03.png" time="031"/>

<a sync="" text="インシネレート" notice="" icon="Targetaoe03.png" time="035"/>

<a sync="兵貴神速……「炎獄の楔」にて" text="セリフ" notice="" icon="Dialog.png" time="037"/>

<a sync="Added new combatant 炎獄の楔" text="●楔POP" notice="次、楔ポップ" icon="" time="041"/>

<a sync="イフリートは「灼熱の咆吼」の" text="★灼熱の咆吼" notice="灼熱注意ー" icon="Fire.png" time="046"/>

<a sync="イフリートは「エラプション」の" text="エラプション" notice="" icon="AOE.png" time="051"/>

<a sync="" text="灼熱爆発" notice="" icon="Explosion.png" time="055" notice-o="-2"/>

<a sync="" text="灼熱爆発" notice="" icon="Explosion.png" time="061" notice-o="-2"/>

<a sync="因果応報……我が炎は" text="セリフ" notice="" icon="Dialog.png" time="070"/>

<a sync="イフリートは「地獄の火炎」の" text="地獄の火炎２" notice="" icon="AllRangeAtk.png" time="075"/>


-<a sync="" text="次の誘導1" notice="次、アルファ、ブラボーえー" icon="" time="078">


-<expressions>

<pre value="1" name="pattern"/>

</expressions>

<v-notice text="➜ ＡＢ" icon="Avoid.png" duration-visible="false" duration="9"/>

</a>


-<a sync="" text="次の誘導2" notice="次、アルファ、ブラボーえー" icon="" time="078">


-<expressions>

<pre value="2" name="pattern"/>

</expressions>

<v-notice text="➜ ＡＢ" icon="Avoid.png" duration-visible="false" duration="9"/>

</a>


-<a sync="" text="次の誘導3" notice="次、ブラボー、チャーリーえー" icon="" time="078">


-<expressions>

<pre value="3" name="pattern"/>

</expressions>

<v-notice text="➜ ＢＣ" icon="Avoid.png" duration-visible="false" duration="9"/>

</a>


-<a sync="" text="次の誘導4" notice="次、ブラボー、チャーリーえー" icon="" time="078">


-<expressions>

<pre value="4" name="pattern"/>

</expressions>

<v-notice text="➜ ＢＣ" icon="Avoid.png" duration-visible="false" duration="9"/>

</a>


-<a sync="" text="次の誘導5" notice="次、チャーリー、デルタえー" icon="" time="078">


-<expressions>

<pre value="5" name="pattern"/>

</expressions>

<v-notice text="➜ ＣＤ" icon="Avoid.png" duration-visible="false" duration="9"/>

</a>


-<a sync="" text="次の誘導6" notice="次、チャーリー、デルタえー" icon="" time="078">


-<expressions>

<pre value="6" name="pattern"/>

</expressions>

<v-notice text="➜ ＣＤ" icon="Avoid.png" duration-visible="false" duration="9"/>

</a>


-<a sync="" text="次の誘導7" notice="次、アルファ、デルタえー" icon="" time="078">


-<expressions>

<pre value="7" name="pattern"/>

</expressions>

<v-notice text="➜ ＡＤ" icon="Avoid.png" duration-visible="false" duration="9"/>

</a>


-<a sync="" text="次の誘導8" notice="次、アルファ、デルタえー" icon="" time="078">


-<expressions>

<pre value="8" name="pattern"/>

</expressions>

<v-notice text="➜ ＡＤ" icon="Avoid.png" duration-visible="false" duration="9"/>

</a>

<a sync="イフリートは「灼熱の咆吼」の" text="★灼熱の咆吼" notice="灼熱注意ー" icon="Fire.png" time="084"/>

<a sync="" text="セットアップ" notice="" icon="SpreadB.png" time="084"/>

<a sync="イフリートは「エラプション」の" text="エラプション" notice="" icon="AOE.png" time="090"/>

<a sync="using クリムゾンサイクロン" text="十字クリサイ" notice="次、十字突進" icon="Avoid.png" time="097"/>


-<a sync="イフリートは「灼熱の咆吼」の" text="★灼熱の咆吼" notice="次、ヒーラーY字" icon="Fire.png" time="103">

<v-notice text="➜ Ｙ字" icon="Arrow5" duration-visible="false" duration="4" order="-1" style="NOTICE_NORMAL_SMALL"/>

</a>

<a sync="" text="灼熱爆発" notice="" icon="Explosion.png" time="109" notice-o="-2"/>

<a sync="イフリートの「フレイムクラッ" text="フレイムクラッシュ" notice="次、正面で頭割り" icon="DamageShare.png" time="115"/>


-<a sync="" notice="" icon="" name="移動のカンペ" time="115" notice-o="1">


-<expressions>

<pre value="false" name="heat"/>

</expressions>

<v-notice text="近くが青➙ ２コマ" icon="TurnR.png" duration-visible="false" duration="20" order="1"/>

<v-notice text="遠くが青➙ １コマ" icon="TurnR.png" duration-visible="false" duration="20" order="2"/>

</a>

<a sync="イフリートは「クリムゾンサイク" text="四連クリサイ" notice="スプリント準備" icon="Avoid.png" time="123" notice-o="-6"/>

<a sync="" text="灼熱注意" notice="" icon="" time="130"/>

<a sync="イフリートの「インシネレート」" text="インシネレート" notice="次、インシネ" icon="Targetaoe03.png" time="137" notice-o="-6"/>

<a sync="" text="インシネレート" notice="" icon="Targetaoe03.png" time="140"/>

<a sync="" text="インシネレート" notice="" icon="Targetaoe03.png" time="143"/>

<a sync="イフリートは「エラプション」の" text="エラプション" notice="" icon="AOE.png" time="152"/>

<a sync="イフリートの「フレイムクラ" text="フレイムクラッシュ" notice="次、正面で頭割り" icon="DamageShare.png" time="165"/>

<a sync="" text="時間切れ" notice="" icon="Timeout.png" time="168" notice-o="0"/>

</s>


-<s name="タイタンフェーズ">

<!-- 優先度ジェイル トリガ start -->

@{var jail_order = new string[] { "[GNB]", "[DRG]", "[PLD]", "[SMN]", "[MCN]", "[DNC]", "[WHM]", "[AST]" };var jail_order_call = new string[] { "あん", "なー", "さむ", "がく", "せんせー", "しょう", "くろ", "しじん" };} 

-<t sync=":グラナイト・ジェイル:........:@jail_order[0]:" text="$1" notice="@jail_order_call[0]" notice-sync="true" no="1">

<v-notice duration-visible="false" duration="5" job-icon="true" order="1"/>

</t>


-<t sync=":グラナイト・ジェイル:........:@jail_order[1]:" text="$1" notice="@jail_order_call[1]" notice-sync="true" no="2">

<v-notice duration-visible="false" duration="5" job-icon="true" order="2"/>

</t>


-<t sync=":グラナイト・ジェイル:........:@jail_order[2]:" text="$1" notice="@jail_order_call[2]" notice-sync="true" no="3">

<v-notice duration-visible="false" duration="5" job-icon="true" order="3"/>

</t>


-<t sync=":グラナイト・ジェイル:........:@jail_order[3]:" text="$1" notice="@jail_order_call[3]" notice-sync="true" no="4">

<v-notice duration-visible="false" duration="5" job-icon="true" order="4"/>

</t>


-<t sync=":グラナイト・ジェイル:........:@jail_order[4]:" text="$1" notice="@jail_order_call[4]" notice-sync="true" no="5">

<v-notice duration-visible="false" duration="5" job-icon="true" order="5"/>

</t>


-<t sync=":グラナイト・ジェイル:........:@jail_order[5]:" text="$1" notice="@jail_order_call[5]" notice-sync="true" no="6">

<v-notice duration-visible="false" duration="5" job-icon="true" order="6"/>

</t>


-<t sync=":グラナイト・ジェイル:........:@jail_order[6]:" text="$1" notice="@jail_order_call[6]" notice-sync="true" no="7">

<v-notice duration-visible="false" duration="5" job-icon="true" order="7"/>

</t>


-<t sync=":グラナイト・ジェイル:........:@jail_order[7]:" text="$1" notice="@jail_order_call[7]" notice-sync="true" no="8">

<v-notice duration-visible="false" duration="5" job-icon="true" order="8"/>

</t>

<t sync=":グラナイト・ジェイル:........:[mex]:" notice="自分にジェイル" name="自分にジェイル" notice-sync="true" no="11"/>

<t sync=":グラナイト・ジェイル:........:[nex]:" notice="ジェイルなし" sync-count="3" name="ジェイルなし" notice-sync="true" no="12"/>

<!-- 優先度ジェイル トリガ end -->


<!-- psync ボムトリガー start -->



-<t text="ボム1➜ 左へ" notice="左えー。" sync-count="1">


-<expressions>

<pre value="false" name="sorted_jail"/>

<set value="true" name="sorted_jail"/>

</expressions>


-<p-sync interval="10">

<combatant name="ボムボルダー" tolerance="0.01" Z="0.00" Y="23.26" X="23.40"/>

<combatant name="ボムボルダー" tolerance="0.01" Z="0.00" Y="23.40" X="23.40"/>

<combatant name="ボムボルダー" tolerance="0.01" Z="0.00" Y="23.40" X="23.60"/>

<combatant name="ボムボルダー" tolerance="0.01" Z="0.00" Y="23.28" X="23.72"/>

<combatant name="ボムボルダー" tolerance="0.01" Z="0.00" Y="23.28" X="23.28"/>

</p-sync>

<v-notice icon="Arrow6" duration-visible="false" duration="5"/>

</t>


-<t text="ボム2➜ 右へ" notice="右えー。" sync-count="1">


-<expressions>

<pre value="false" name="sorted_jail"/>

<set value="true" name="sorted_jail"/>

</expressions>


-<p-sync interval="10">

<combatant name="ボムボルダー" tolerance="0.01" Z="0.00" Y="23.26" X="23.60"/>

<combatant name="ボムボルダー" tolerance="0.01" Z="0.00" Y="23.40" X="23.40"/>

<combatant name="ボムボルダー" tolerance="0.01" Z="0.00" Y="23.40" X="23.60"/>

<combatant name="ボムボルダー" tolerance="0.01" Z="0.00" Y="23.28" X="23.72"/>

<combatant name="ボムボルダー" tolerance="0.01" Z="0.00" Y="23.28" X="23.28"/>

</p-sync>

<v-notice icon="Arrow4" duration-visible="false" duration="5"/>

</t>


-<t text="ボム3➜ 左へ" notice="左えー。" sync-count="1">


-<expressions>

<pre value="false" name="sorted_jail"/>

<set value="true" name="sorted_jail"/>

</expressions>


-<p-sync interval="10">

<combatant name="ボムボルダー" tolerance="0.01" Z="0.00" Y="23.40" X="23.74"/>

<combatant name="ボムボルダー" tolerance="0.01" Z="0.00" Y="23.28" X="23.72"/>

<combatant name="ボムボルダー" tolerance="0.01" Z="0.00" Y="23.40" X="23.60"/>

<combatant name="ボムボルダー" tolerance="0.01" Z="0.00" Y="23.60" X="23.60"/>

<combatant name="ボムボルダー" tolerance="0.01" Z="0.00" Y="23.72" X="23.72"/>

</p-sync>

<v-notice icon="Arrow6" duration-visible="false" duration="5"/>

</t>


-<t text="ボム4➜ 右へ" notice="右えー。" sync-count="1">


-<expressions>

<pre value="false" name="sorted_jail"/>

<set value="true" name="sorted_jail"/>

</expressions>


-<p-sync interval="10">

<combatant name="ボムボルダー" tolerance="0.01" Z="0.00" Y="23.60" X="23.74"/>

<combatant name="ボムボルダー" tolerance="0.01" Z="0.00" Y="23.28" X="23.72"/>

<combatant name="ボムボルダー" tolerance="0.01" Z="0.00" Y="23.40" X="23.60"/>

<combatant name="ボムボルダー" tolerance="0.01" Z="0.00" Y="23.60" X="23.60"/>

<combatant name="ボムボルダー" tolerance="0.01" Z="0.00" Y="23.72" X="23.72"/>

</p-sync>

<v-notice icon="Arrow4" duration-visible="false" duration="5"/>

</t>


-<t text="ボム5➜ 左へ" notice="左えー。" sync-count="1">


-<expressions>

<pre value="false" name="sorted_jail"/>

<set value="true" name="sorted_jail"/>

</expressions>


-<p-sync interval="10">

<combatant name="ボムボルダー" tolerance="0.01" Z="0.00" Y="23.74" X="23.60"/>

<combatant name="ボムボルダー" tolerance="0.01" Z="0.00" Y="23.72" X="23.28"/>

<combatant name="ボムボルダー" tolerance="0.01" Z="0.00" Y="23.72" X="23.72"/>

<combatant name="ボムボルダー" tolerance="0.01" Z="0.00" Y="23.60" X="23.60"/>

<combatant name="ボムボルダー" tolerance="0.01" Z="0.00" Y="23.60" X="23.40"/>

</p-sync>

<v-notice icon="Arrow6" duration-visible="false" duration="5"/>

</t>


-<t text="ボム6➜ 右へ" notice="右えー。" sync-count="1">


-<expressions>

<pre value="false" name="sorted_jail"/>

<set value="true" name="sorted_jail"/>

</expressions>


-<p-sync interval="10">

<combatant name="ボムボルダー" tolerance="0.01" Z="0.00" Y="23.74" X="23.40"/>

<combatant name="ボムボルダー" tolerance="0.01" Z="0.00" Y="23.72" X="23.28"/>

<combatant name="ボムボルダー" tolerance="0.01" Z="0.00" Y="23.72" X="23.72"/>

<combatant name="ボムボルダー" tolerance="0.01" Z="0.00" Y="23.60" X="23.60"/>

<combatant name="ボムボルダー" tolerance="0.01" Z="0.00" Y="23.60" X="23.40"/>

</p-sync>

<v-notice icon="Arrow4" duration-visible="false" duration="5"/>

</t>


-<t text="ボム7➜ 左へ" notice="左えー。" sync-count="1">


-<expressions>

<pre value="false" name="sorted_jail"/>

<set value="true" name="sorted_jail"/>

</expressions>


-<p-sync interval="10">

<combatant name="ボムボルダー" tolerance="0.01" Z="0.00" Y="23.60" X="23.26"/>

<combatant name="ボムボルダー" tolerance="0.01" Z="0.00" Y="23.72" X="23.28"/>

<combatant name="ボムボルダー" tolerance="0.01" Z="0.00" Y="23.40" X="23.40"/>

<combatant name="ボムボルダー" tolerance="0.01" Z="0.00" Y="23.60" X="23.40"/>

<combatant name="ボムボルダー" tolerance="0.01" Z="0.00" Y="23.28" X="23.28"/>

</p-sync>

<v-notice icon="Arrow6" duration-visible="false" duration="5"/>

</t>


-<t text="ボム8➜ 右へ" notice="右えー。" sync-count="1">


-<expressions>

<pre value="false" name="sorted_jail"/>

<set value="true" name="sorted_jail"/>

</expressions>


-<p-sync interval="10">

<combatant name="ボムボルダー" tolerance="0.01" Z="0.00" Y="23.40" X="23.26"/>

<combatant name="ボムボルダー" tolerance="0.01" Z="0.00" Y="23.72" X="23.28"/>

<combatant name="ボムボルダー" tolerance="0.01" Z="0.00" Y="23.40" X="23.40"/>

<combatant name="ボムボルダー" tolerance="0.01" Z="0.00" Y="23.60" X="23.40"/>

<combatant name="ボムボルダー" tolerance="0.01" Z="0.00" Y="23.28" X="23.28"/>

</p-sync>

<v-notice icon="Arrow4" duration-visible="false" duration="5"/>

</t>

<!-- psync ボムトリガー end -->


<a sync="starts using ジオクラッシュ" text="ジオクラッシュ1" notice="ジオクラ" icon="" time="003" notice-o="1"/>

<a sync="" text="覚醒確認" notice="" icon="覚醒.png" time="005"/>

<a sync="「大地の怒り」に砕け散れぇぇ" text="セリフ" notice="" icon="Dialog.png" time="008"/>

<a sync="「大地の怒り」の構え" text="大地の怒り" notice="次、大地の怒り" icon="HardAllRngAtk.png" time="009"/>

<a sync="横暴なるヒトの子よ…… お主を屠" text="セリフ" notice="" icon="Dialog.png" time="016"/>

<a sync="タイタンの「ロックバスター」" text="ロックバスター" notice="次、MT大ダメージ" icon="HardAttack.png" time="020"/>


-<a sync="タイタンの「マウンテンバスタ" text="マウンテンバスター" notice="" icon="Targetaoe03.png" time="023">

<v-notice text="マウンテン" icon="HardAttack.png" duration-visible="false" duration="5"/>

</a>

<a sync="" text="大地の重みx2" notice="次、2連重み、右、左" icon="StackAOE.png" time="024"/>

<a sync="タイタンの「ジオクラッシュ」" text="ジオクラッシュ2" notice="次、ジオクラからホールインワン" icon="AllRangeAtk.png" time="033"/>

<a sync="タイタンは「大激震」の構え" text="大激震" notice="" icon="KnockBack.png" time="040"/>

<a sync="" text="ボムボルダー" notice="" icon="Bomb.png" time="042"/>


-<a sync="" text="大爆発" notice="爆発したら中心えー" icon="Explosion.png" time="047" notice-o="-4">

<v-notice text="中心線へ" icon="Arrow1.png" duration-visible="false" duration="3" order="20"/>

</a>

<a sync="タイタンの「グラナイト・" text="グラナイト・ジェイル" notice="" icon="" time="047"/>

<a sync="" text="ランドスライド(1)" notice="" icon="Avoid.png" time="051"/>

<a sync="" text="ランドスライド(2)" notice="" icon="Avoin.png" time="054"/>

<a sync="" text="激震x8" notice="次、激震" icon="AllRangeAtk.png" time="057"/>

<a sync="" text="大地の重みx2" notice="次、2連重み、前、右" icon="StackAOE.png" time="069"/>

<a sync="" text="ランドスライド(1)" notice="次、見えないランスラ" icon="Avoid.png" time="076"/>

<a sync="" text="ランドスライド(2)" notice="" icon="Avoid.png" time="079" notice-o=""/>

<a sync="" text="ジオクラッシュ3" notice="次、ジオクラ" icon="AllRangeAtk.png" time="087"/>

<a sync="タイタンの「グラナイト・" text="グラナイト・ジェイル" notice="次、ヒーラージェイル" icon="" time="093"/>

<a sync="" text="ランドスライド(1)" notice="次、見えないランスラ" icon="Avoid.png" time="105"/>

<a sync="" text="ランドスライド(2)" notice="" icon="Avoid.png" time="108"/>

<a sync="" text="激震x6" notice="次、激震" icon="AllRangeAtk.png" time="111"/>


-<a sync="タイタンの「マウンテンバスタ" text="マウンテンバスター" notice="次、ST大ダメージ" icon="Targetaoe03.png" time="123">

<v-notice text="マウンテン" icon="HardAttack.png" duration-visible="false" duration="5"/>

</a>

<a sync="" text="大地の重みx3" notice="次、3連重み" icon="StackAOE.png" time="127"/>

<a sync="" text="ランドスライドx2" notice="次、見えないランスラ" icon="Avoid.png" time="133"/>

<a sync="タイタンの「ロックバスター" text="ロックバスター" notice="次、MT大ダメージ" icon="HardAttack.png" time="140"/>


-<a sync="タイタンの「マウンテンバスタ" text="マウンテンバスター" notice="" icon="Targetaoe03.png" time="144">

<v-notice text="マウンテン" icon="HardAttack.png" duration-visible="false" duration="5"/>

</a>

<a sync="" text="大地の重みx3" notice="次、3連重み、右、左、右" icon="StackAOE.png" time="145"/>

<a sync="" text="激震x8" notice="次、激震" icon="AllRangeAtk.png" time="156"/>

<a sync="" text="時間切れ" notice="" icon="Timeout.png" time="171" notice-o="0"/>

</s>


-<s name="中継フェーズ">

<a sync="" text="覚醒確認" notice="" icon="覚醒.png" time="002"/>

<a sync="魔導ビットは「自爆」の構え。" text="自爆" notice="次、キャスLB" icon="Distance.png" time="011"/>

<a sync="光の使徒よ、消え去るがいい！" text="死の宣告" notice="次、ヒーラーLB" icon="" time="024"/>

<a sync="starts using ダージャ" text="ダージャ" notice="次、近接LB" icon="" time="034"/>

<a sync="やってくれる…… だが、アルテマウェポンの真の力、見くびってくれるなよ！" text="捨て台詞" notice="" icon="Dialog.png" time="046"/>

<a sync="渦なす生命の色、七つの扉開き、力の塔の天に至らん！ ……アルテマッ！" text="アルテマ" notice="次、タンクLB" icon="AllRangeAtk.png" time="051"/>

<a sync="フハハハハハハ！ 絶望の暗き底へと沈むがいい！" text="アルテマフェーズ開始" notice="" icon="" time="061"/>


-<a sync="" text="タゲ可能まで10" notice="10秒前！" icon="" time="085" notice-o="0">

<v-notice text="１０秒前" icon="True.png" duration="9.6"/>

</a>

<a sync="ウェポンの「魔導フレア」" text="魔導フレア" notice="" icon="HardAllRngAtk.png" time="095" notice-o="0"/>

<a sync="ウェポンの「吸着式エーテル" text="吸着式エーテル爆雷" notice="" icon="Targetaoe01.png" time="097"/>

<a sync="ウェポンは「誘導レーザー」" text="誘導レーザー" notice="" icon="Targetaoe01.png" time="098" notice-o="0"/>

</s>


-<s name="追撃の究極幻想">


-<t sync="^1A:[id8]:[pc] gains the effect of 地神のミンネ" text="${_pc}\n← ミンネ" notice="ミンネ">

<v-notice duration-visible="false" duration="5" job-icon="true" order="-1"/>

</t>

<!--追撃の前半の逃げる方向についてガルの出現位置によって → 2方向に限定されるタイタンの出現位置によって → 3方向に限定されるこのうち、ガルからの意見とタイタンからの意見が2票以上入った方向が正解である。それを明示する。 -->


<!-- ガル北東 -->



-<t sync-count="1" name="toC/D">


-<p-sync>

<combatant name="ガルーダ" tolerance="0.01" Z="0.00" Y="23.44" X="23.56"/>

</p-sync>


-<expressions>

<set name="toC" count="+1"/>

<set name="toD" count="+1"/>

</expressions>

</t>

<!-- ガル南東 -->



-<t sync-count="1" name="toA/D">


-<p-sync>

<combatant name="ガルーダ" tolerance="0.01" Z="0.00" Y="23.56" X="23.56"/>

</p-sync>


-<expressions>

<set name="toA" count="+1"/>

<set name="toD" count="+1"/>

</expressions>

</t>

<!-- ガル南西 -->



-<t sync-count="1" name="toA/B">


-<p-sync>

<combatant name="ガルーダ" tolerance="0.01" Z="0.00" Y="23.56" X="23.44"/>

</p-sync>


-<expressions>

<set name="toA" count="+1"/>

<set name="toB" count="+1"/>

</expressions>

</t>

<!-- ガル北西 -->



-<t sync-count="1" name="toB/C">


-<p-sync>

<combatant name="ガルーダ" tolerance="0.01" Z="0.00" Y="23.44" X="23.44"/>

</p-sync>


-<expressions>

<set name="toB" count="+1"/>

<set name="toC" count="+1"/>

</expressions>

</t>

<!-- タイタンA -->



-<t sync-count="1" name="toBCD">


-<p-sync>

<combatant name="タイタン" tolerance="0.06" Z="0.00" Y="23.16" X="23.50"/>

</p-sync>


-<expressions>

<set name="toB" count="+1"/>

<set name="toC" count="+1"/>

<set name="toD" count="+1"/>

</expressions>

</t>

<!-- タイタンB -->



-<t sync-count="1" name="toACD">


-<p-sync>

<combatant name="タイタン" tolerance="0.06" Z="0.00" Y="23.50" X="23.84"/>

</p-sync>


-<expressions>

<set name="toA" count="+1"/>

<set name="toC" count="+1"/>

<set name="toD" count="+1"/>

</expressions>

</t>

<!-- タイタンC -->



-<t sync-count="1" name="toABD">


-<p-sync>

<combatant name="タイタン" tolerance="0.06" Z="0.00" Y="23.84" X="23.50"/>

</p-sync>


-<expressions>

<set name="toA" count="+1"/>

<set name="toB" count="+1"/>

<set name="toD" count="+1"/>

</expressions>

</t>

<!-- タイタンD -->



-<t sync-count="1" name="toABC">


-<p-sync>

<combatant name="タイタン" tolerance="0.06" Z="0.00" Y="23.50" X="23.16"/>

</p-sync>


-<expressions>

<set name="toA" count="+1"/>

<set name="toB" count="+1"/>

<set name="toC" count="+1"/>

</expressions>

</t>

<!-- Aへ決定 -->



-<t sync="decide_to_direction" notice="アルファえー" name="toA" no="1">


-<expressions>

<pre name="toA" count="2"/>

<pre value="false" name="decided_direction"/>

<set value="true" name="decided_direction"/>

</expressions>

<v-notice text="Ａへ" icon="A" duration-visible="false" duration="30" order="1" sync-to-hide=":アルテマウェポン:2B7C:セルレアムベント:"/>

</t>

<!-- Bへ決定 -->



-<t sync="decide_to_direction" notice="ブラボーえー" name="toB" no="2">


-<expressions>

<pre name="toB" count="2"/>

<pre value="false" name="decided_direction"/>

<set value="true" name="decided_direction"/>

</expressions>

<v-notice text="Ｂへ" icon="B" duration-visible="false" duration="30" order="1" sync-to-hide=":アルテマウェポン:2B7C:セルレアムベント:"/>

</t>

<!-- Cへ決定 -->



-<t sync="decide_to_direction" notice="チャーリーえー" name="toC" no="3">


-<expressions>

<pre name="toC" count="2"/>

<pre value="false" name="decided_direction"/>

<set value="true" name="decided_direction"/>

</expressions>

<v-notice text="Ｃへ" icon="C" duration-visible="false" duration="30" order="1" sync-to-hide=":アルテマウェポン:2B7C:セルレアムベント:"/>

</t>

<!-- Dへ決定 -->



-<t sync="decide_to_direction" notice="デルタえー" name="toD" no="4">


-<expressions>

<pre name="toD" count="2"/>

<pre value="false" name="decided_direction"/>

<set value="true" name="decided_direction"/>

</expressions>

<v-notice text="Ｄへ" icon="D" duration-visible="false" duration="30" order="1" sync-to-hide=":アルテマウェポン:2B7C:セルレアムベント:"/>

</t>

<a sync="アルテマウェポンは「追撃の究極幻想」の構え。" text="追撃の究極幻想" notice="" icon="" time="001" notice-o="0"/>

<a sync="アルテマウェポンの「追撃の究極幻想」" notice="" icon="" name="追撃の究極幻想の発動" time="007"/>


-<a text="行き先の確定" time="010">

<dump log="decide_to_direction" target="Log"/>

</a>

<a sync="starts using クリムゾンサイク" text="[イフ]突進+[ガル]嵐" notice="" icon="" time="015"/>

<a sync="" text="ランドスライド" notice="" icon="" time="016"/>

<a sync="" text="不可視ランドスライド" notice="" icon="" time="018"/>

<a sync=":アルテマウェポン:2B7C:セルレアムベント:" text="セルレアムベント" notice="フェザー注意、動くな" icon="" time="020" notice-o="0"/>

<a sync="" text="フェザーレイン" notice="次、エラプ誘導、他はアルファえ" icon="" time="023" notice-o="1"/>

<a sync="" text="エラプション" notice="" icon="" time="036"/>

<a sync="ポンは「光輝の炎柱」の構え。" text="光輝の炎柱" notice="次、サラミのきわえー" icon="" time="046"/>

<a sync="" text="ランドスライド" notice="" icon="" time="051"/>

<a sync="" text="不可視ランスラ" notice="" icon="" time="053"/>

<a sync="" text="激震" notice="" icon="" time="058"/>

<a sync="ウェポンの「吸着式エーテル爆雷」" text="吸着式エーテル爆雷" notice="次、爆雷" icon="" time="060"/>

<a sync="start using ミストラルシュリーク" text="ミストラルシュリーク" notice="次、全体攻撃" icon="" time="065"/>

<a sync="" text="フェザーレイン" notice="" icon="" time="069"/>

<a sync="ポンは「誘導レーザー」の構え。" text="誘導レーザー" notice="次、ST大ダメージ" icon="" time="070"/>

<a sync="" text="フェザーレイン" notice="" icon="" time="073"/>

</s>


-<s name="爆撃の究極幻想">


-<t sync="starts using 大地の重み" name="爆撃フラグ">


-<expressions>

<set value="true" name="in_bakugeki"/>

</expressions>

</t>

<a sync="starts using 爆撃の究極幻想" text="爆撃の究極幻想" icon="" time="001"/>

<a sync="" text="大地の重み1" notice="次、重み、右、左、前" icon="" time="012"/>

<a sync="" text="大地の重み2" notice="" icon="" time="015"/>

<a sync="" text="フレイムクラッシュ" notice="" icon="" time="016"/>

<a sync="" text="緑線" notice="" icon="" time="017"/>

<a sync="" text="緑玉1" notice="" icon="" time="017"/>

<a sync="" text="大地の重み3" notice="" icon="" time="018"/>

<a sync="" text="灼熱" notice="" icon="" time="019"/>

<a sync="" text="緑玉2" notice="" icon="" time="023"/>

<a sync="" text="フェザーレイン" notice="フェザー！" icon="" time="024"/>

<a sync="starts using クリムゾンサイク" text="クリムゾンサイクロン" notice="" icon="" time="026"/>

<a sync="" text="ランドスライド" notice="" icon="" time="028"/>

<a sync="" text="[イフ]突進" notice="" icon="" time="029"/>

<a sync="" text="緑玉3" notice="" icon="" time="029"/>

<a sync="" text="炎＋嵐＋ランスラ" notice="" icon="" time="030"/>

<a sync="" text="緑玉4" notice="" icon="" time="036"/>

<a sync="アルテマウェポンの「魔導フレア」" text="魔導フレア" notice="" icon="HardAllRngAtk.png" time="036" notice-o="-6"/>

<a sync="starts using フェザーレイン" text="フェザーレイン" notice="フェザー！" icon="" time="041"/>

<a sync="ポンは「誘導レーザー」の構え。" text="誘導レーザー" notice="次、誘導レーザー" icon="" time="054" notice-o="-6"/>

<a sync="starts using 光輝の炎柱" text="光輝の炎柱" notice="次、サラミ、拡散、バルカン" icon="" time="064"/>

<a sync="ウェポンの「拡散レーザー」" text="拡散レーザー" notice="" icon="" time="069"/>


-<a sync="イフリートの「バルカン" text="バルカン" notice="次、バルカン" icon="KnockBack.png" time="072" notice-o="-5" sync-e="5" sync-s="-5">

<v-notice text="バルカン" icon="True" duration-visible="false" duration="4" order="2" style="NOTICE_NORMAL_SMALL"/>

</a>


-<a text="バースト" notice="ここでバースト" icon="Check.png" time="073" notice-o="-1">

<v-notice text="バースト！" icon="True" duration-visible="true" duration="4" style="NOTICE_NORMAL_SMALL"/>

</a>

<a sync="ポンは「誘導レーザー」の構え。" text="誘導レーザー" notice="次、ST大ダメージからバルカン" icon="" time="077" notice-o="-3" sync-e="5" sync-s="-5"/>


-<a sync="イフリートの「バルカン" text="バルカン" notice="" icon="KnockBack.png" time="082" sync-e="5" sync-s="-5">

<v-notice text="バルカン" icon="True" duration-visible="false" duration="4" order="2" style="NOTICE_NORMAL_SMALL"/>

</a>

<a sync="ウェポンの「拡散レーザー」" text="拡散レーザー" notice="次、MT大ダメージ" icon="" time="087" sync-e="5" sync-s="-5"/>

</s>


-<s name="乱撃の究極幻想">

<!-- ジェイル担当 -->



-<t sync=":グラナイト・ジェイル:[id8]:[mex]:0:" text="ジェイル➜ Ａ" notice="自分にジェイル">

<v-notice icon="A.png" duration-visible="false" duration="4" order="1"/>

</t>


-<t sync=":グラナイト・ジェイル:[id8]:[nex]:0:" text="ジェイルなし" notice="ジェイルなし">

<v-notice icon="Check.png" duration-visible="false" duration="4" order="1" style="NOTICE_NORMAL"/>

</t>


-<t sync="^1A:[id8]:[pc] gains the effect of 地神のミンネ" text="${_pc}\n← ミンネ" notice="ミンネ">

<v-notice duration-visible="false" duration="5" job-icon="true" order="-1"/>

</t>

<!-- 乱撃タイムライン -->


<a sync="starts using 乱撃の究極幻想" text="乱撃の究極幻想" notice="" icon="" time="000" notice-o="0"/>

<a sync="ウェポンの「乱撃の究極幻想」" text="乱撃の究極幻想" notice="" icon="" time="006" notice-o="-3"/>

<a sync="" text="エラプション1" notice="" icon="" time="012"/>

<a sync="" text="エラプション2" notice="" icon="" time="014"/>

<a sync="" text="エラプション3" notice="" icon="" time="016"/>

<a sync="" text="リヒト1" notice="" icon="" time="018"/>

<a sync="" text="エラプ4+リヒト2" notice="" icon="" time="018"/>

<a sync="starts using ミストラルソング on ガルーダ." text="ミストラルソング" notice="" icon="" time="019" notice-o="0"/>

<a sync="Added new combatant. name=グラナイト・ジェイル" text="ジェイル化" notice="" icon="" time="021" notice-o="0"/>

<a sync="" text="フェザーレイン" notice="" icon="" time="023"/>

<a sync="" text="フェザーレイン" notice="" icon="" time="025"/>

<a sync="" text="リヒト最後" notice="" icon="" time="028"/>

<a sync="" text="ランスラ＋メソハイ" notice="" icon="" time="030"/>

<a sync="" text="ランスラ＋頭割り" notice="" icon="" time="033"/>

<a sync="" text="フェザーレイン" notice="フェザー！" icon="" time="040"/>

<a sync="アルテマウェポンの「魔導フレア」" text="魔導フレア" notice="" icon="" time="041"/>

<a sync="アルテマウェポンは「アルテマ」の構え。" text="アルテマ開始" notice="次、フルバリア" icon="" time="054" notice-o="-6"/>


-<a sync="アルテマウェポンは「エーテル波動」の構え。" text="エーテル波動" notice="" icon="" time="058">

<v-notice text="フルバリア" icon="True" duration-visible="false" duration="4" style="NOTICE_NORMAL_SMALL"/>

</a>
@if (Model.Player.InJob("DRK")) { 

-<a sync="" text="ノックバック" notice="右上えー" icon="Knockback.png" time="062">

<v-notice text="右上へ" icon="Arrow2" duration-visible="false" duration="5"/>

</a>
}@if (Model.Player.InJob("PLD")) { 

-<a sync="" text="ノックバック" notice="右下えー" icon="Knockback.png" time="062">

<v-notice text="右下へ" icon="Arrow4" duration-visible="false" duration="5"/>

</a>
} 
<!--<a time="062" text="ノックバック" icon="Knockback.png" sync="" notice="左上えー"><v-notice text="左上へ" icon="Arrow8" duration="5" duration-visible="false" /></a> -->

@if (Model.Player.InRole("DPS", "HEALER")) { 

-<a sync="" text="ノックバック" notice="左下えー" icon="Knockback.png" time="062">

<v-notice text="左下へ" icon="Arrow6" duration-visible="false" duration="5"/>

</a>
} 
<a sync="" text="アルテマ爆雷出現" notice="" icon="" time="064"/>


-<a sync="" text="12時集合" notice="12時えー" icon="" time="077">

<v-notice text="12時へ" icon="Arrow1" duration-visible="false" duration="5" order="1"/>

</a>

<a sync="ウェポンの「吸着爆雷」" text="吸着爆雷" notice="" icon="" time="083"/>

<t goto="ラストガルーダ" sync="^14:2CD3:アルテマウェポン starts using" text="ガルーダ" notice="次、ガルーダ"/>

<t goto="ラストイフリート" sync="^14:2CD4:アルテマウェポン starts using" text="イフリート" notice="次、イフリート"/>

<t goto="ラストタイタン" sync="^14:2CD5:アルテマウェポン starts using" text="タイタン" notice="次、タイタン"/>

</s>

<!-- ラストガルーダ -->



-<s name="ラストガルーダ">


-<a name="Flag" time="000">


-<expressions>

<set value="true" name="done_Garuda"/>

</expressions>

</a>


-<a sync="" text="ウィケッドホイール" notice="待機、その後アルファえー" icon="Leave.png" time="006">

<v-notice text="待機→Ａ" icon="Arrow8.png" duration-visible="false" duration="4"/>

</a>

<a sync="の「吸着爆雷」が切れた。" text="吸着爆雷起爆" notice="次、全体攻撃" icon="DamageShare.png" time="009" notice-o="-3"/>


-<a sync="ガルーダ starts using エリアルブラスト on ガルーダ" text="エリアルブラスト" notice="終わったら12時に戻る、フェザー注意" icon="HardAllRngAtk.png" time="013" notice-o="-1">

<v-notice text="12時に戻る" icon="Avoid.png" duration-visible="false" duration="5"/>

</a>

<a goto="最終フェーズ" text="最終フェーズへ" notice="" icon="Check.png" time="026"/>

<t goto="ラストイフリート" sync="^14:2CD4:アルテマウェポン starts using" text="イフリート" notice="次、イフリート"/>

<t goto="ラストタイタン" sync="^14:2CD5:アルテマウェポン starts using" text="タイタン" notice="次、タイタン"/>

</s>

<!-- ラストイフリート -->



-<s name="ラストイフリート">


-<a name="Flag" time="000">


-<expressions>

<set value="true" name="done_Ifrit"/>

</expressions>

</a>


-<a sync="" text="エラプション" notice="右斜め前えー" icon="AOE.png" time="006">

<v-notice text="右斜め前へ" icon="Arrow2.png" duration-visible="false" duration="4"/>

</a>

<a sync="の「吸着爆雷」が切れた。" text="吸着爆雷起爆" notice="次、全体攻撃" icon="DamageShare.png" time="009" notice-o="-3"/>


-<a sync="イフリート starts using 地獄の火炎 on イフリート" text="地獄の火炎" notice="そのままの位置でー" icon="HardAllRngAtk.png" time="013" notice-o="-1">

<v-notice text="そのまま" icon="Avoid.png" duration-visible="false" duration="5"/>

</a>

<a goto="最終フェーズ" text="最終フェーズへ" notice="" icon="Check.png" time="026"/>

<t goto="ラストガルーダ" sync="^14:2CD3:アルテマウェポン starts using" text="ガルーダ" notice="次、ガルーダ"/>

<t goto="ラストタイタン" sync="^14:2CD5:アルテマウェポン starts using" text="タイタン" notice="次、タイタン"/>

</s>

<!-- ラストタイタン -->



-<s name="ラストタイタン">


-<a name="Flag" time="000">


-<expressions>

<set value="true" name="done_Titan"/>

</expressions>

</a>


-<a sync="" text="大地の重み1" notice="重み、右、左、右" icon="StackAOE.png" time="004">

<v-notice text="右➜左➜右" icon="Arrow3.png" duration-visible="false" duration="4"/>

</a>

<a sync="" text="大地の重み2" notice="" icon="StackAOE.png" time="007"/>

<a sync="の「吸着爆雷」が切れた。" text="吸着爆雷起爆" notice="次、全体攻撃" icon="DamageShare.png" time="009" notice-o="-3"/>

<a sync="" text="大地の重み3" notice="" icon="StackAOE.png" time="010"/>

<a sync="タイタン starts using 大地の怒り on タイタン" text="大地の怒り" notice="そのままの位置でー" icon="HardAllRngAtk.png" time="013" notice-o="-1"/>

<a goto="最終フェーズ" text="最終フェーズへ" notice="" icon="Check.png" time="026"/>

<!-- イフリートが終わっている？ -->



-<t sync="starts using 大地の怒り on タイタン" notice="そのまま" name="移動1">


-<expressions>

<pre value="true" name="done_Ifrit"/>

</expressions>

<v-notice text="そのまま" icon="Avoid.png" duration-visible="false" duration="5"/>

</t>

<!-- イフリートが終わっていない？ -->



-<t sync="starts using 大地の怒り on タイタン" notice="終わったら12時えー" name="移動2">


-<expressions>

<pre value="false" name="done_Ifrit"/>

</expressions>

<v-notice text="12時に戻る" icon="Avoid.png" duration-visible="false" duration="5"/>

</t>

<t goto="ラストガルーダ" sync="^14:2CD3:アルテマウェポン starts using" text="ガルーダ" notice="次、ガルーダ"/>

<t goto="ラストイフリート" sync="^14:2CD4:アルテマウェポン starts using" text="イフリート" notice="次、イフリート"/>

</s>


-<s name="最終フェーズ">

<a text="さあ決着をつけようか" time="001"/>


-<a text="薬" notice="薬、使え" icon="Buff.png" time="004" notice-o="-3">

<!-- アルテマエーテル58 -->


<v-notice text="エーテル５８で" icon="True.png" duration-visible="false" duration="2.9" order="30"/>

<v-notice text="薬" icon="Potion.png" duration-visible="false" duration="2.9" order="31" style="NOTICE_NORMAL"/>

</a>

<a sync="「スタン」の効果" text="拉致1" notice="ひとり！" icon="Leave.png" sync-count="1" time="030" notice-o="0" sync-s="-30"/>

<a sync="" text="拉致2" notice="ふたり！" icon="Leave.png" time="033" notice-o="0"/>

<a sync="" text="拉致3" notice="さんにん！" icon="Leave.png" time="036" notice-o="0"/>

<a sync="" text="拉致4" notice="よにん！" icon="Leave.png" time="039" notice-o="0"/>

<a sync="" text="拉致5" notice="後３人！" icon="Leave.png" time="042" notice-o="0"/>

<a sync="" text="拉致6" notice="後２人！" icon="Leave.png" time="045" notice-o="0"/>

<a sync="" text="拉致7" notice="最後！" icon="Leave.png" time="048" notice-o="0"/>

<a sync="" text="拉致8" notice="" icon="Leave.png" time="051" notice-o="0"/>


-<t sync="は、アルテマウェポンを倒した。" notice="完全論破！" name="幻想敗れたり">

<v-notice text="完　全　論　破" icon="True.png" duration-visible="false" duration="20"/>

</t>

</s>

</timeline>
