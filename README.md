# House Prices Prediction with Ensemble Models

Kaggle「House Prices - Advanced Regression Techniques」コンペの学習コードです。  
欠損値補完、外れ値除去、特徴量エンジニアリング、複数モデルのアンサンブルを組み合わせて精度を改善しました。

## このプロジェクトでできること
- **住宅価格の精度予測**（Kaggle House Prices データセット）
- **データ分析**: 欠損値処理・外れ値除去・特徴量エンジニアリング
- **モデリング**: LightGBM・Ridge・Lasso を用いたアンサンブル
- **成果**: CV RMSLE 0.115 / Kaggle LB 0.131

## 環境
- Python 3.12.7
- Jupyter Notebook
- 動作確認: ローカル環境 (Windows 11)

## インストール
依存ライブラリは `requirements.txt` にまとめています。
```bash
pip install -r requirements.txt
```

## プロジェクト概要
- **目的**: 住宅価格（SalePrice）の予測
- **使用データ**: Kaggle House Prices データセット  
- **アプローチ**:(Notebookに主なアプローチ段階のipynbを格納）
- 1. データ解釈
  2. ベースライン作成
     - LinearRegression
     - LightGBM  
  3. モデル解釈として SHAP を用いて重要特徴量を確認
  4. 特徴量エンジニアリング（TotalSF, OverallQual × GrLivArea など）
  5. 欠損値の論理的補完（Garage, Basement, LotFrontage など）
  6. 外れ値の除去（GrLivArea > 4000 & SalePrice < 300000）
  7. One-Hot Encoding によるカテゴリ変数処理
  8. アンサンブル（重み付き平均）
     - LightGBM  
     - Ridge Regression  
     - Lasso Regression  

## モデル精度
- **Cross Validation (CV, KFold 5分割)**  
  - LinearRegression RMSLE: 0.230
  - LightGBM RMSLE: 0.230  
  - **Ensemble RMSLE: 0.115**
- **Kaggle Public LB (Testデータ)**  
  - Score: **0.131**

## 使い方
1. Kaggle から `train.csv` と `test.csv` をダウンロードして、このリポジトリ直下に配置
2. 実行:

```bash
jupyter notebook Final_Ensemble_Model.ipynb
```

## Qiita記事
https://qiita.com/c62323440/items/fd5f1f0bdf22490ba7c6