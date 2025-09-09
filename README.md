# graphRAG-visualization
graphRAG-visualizer


更新图显示，需要更新以下3部分数据：
<script>
    const graphData = {
        entities: ["慢性淋巴细胞白血病", "CLL", "小淋巴细胞淋巴瘤", "SLL", "世界卫生组织", 
                    "WHO", "美国", "中国", "非霍奇金淋巴瘤", "NHL", "B 细胞恶性肿瘤"],
        triples: [
            ["慢性淋巴细胞白血病", "缩写", "CLL"],
            ["小淋巴细胞淋巴瘤", "缩写", "SLL"],
            ["世界卫生组织", "缩写", "WHO"],
            ["慢性淋巴细胞白血病", "属于", "B 细胞恶性肿瘤"],
            ["小淋巴细胞淋巴瘤", "属于", "B 细胞恶性肿瘤"],
            ["慢性淋巴细胞白血病", "与...被WHO分类为同种疾病", "小淋巴细胞淋巴瘤"],
            ["美国", "CLL/SLL年发病率", "XX.XX/XX,XX"],
            ["CLL/SLL", "在美国占白血病新发病例比例", "XX/XX"],
            ["中国", "CLL/SLL发病率", "相对较低"],
            ["CLL/SLL", "在中国占非霍奇金淋巴瘤比例", "XX%～XX%"],
            ["非霍奇金淋巴瘤", "在中国发病率", "XX.XX/XX,XX"]
        ]
    };

    // 实体类型分类函数
    function getNodeType(entity) {
        const diseases = ["慢性淋巴细胞白血病", "CLL", "小淋巴细胞淋巴瘤", "SLL", 
                        "非霍奇金淋巴瘤", "NHL", "白血病", "CLL/SLL", "B 细胞恶性肿瘤"];
        const orgs = ["世界卫生组织", "WHO", "NCCN", "CACA", "ACS", "NCI"];
        const locations = ["美国", "中国"];
        const treatments = ["Bruton 酪氨酸激酶", "BTK", "BTK抑制剂"];
        
        if (diseases.includes(entity)) return "disease";
        if (orgs.includes(entity)) return "organization";
        if (locations.includes(entity)) return "location";
        if (treatments.includes(entity)) return "treatment";
        return "other";
    }

    // 颜色映射
    const colorMap = {
        disease: "#FF6B6B",
        organization: "#4ECDC4",
        location: "#45B7D1",
        treatment: "#FFA07A",
        other: "#98D8C8"
    };
</script>