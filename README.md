function dailyLog187() {
  const metrics = [
    { name: "CPU", usage: 64, limit: 80 },
    { name: "Memory", usage: 72, limit: 85 },
    { name: "Storage", usage: 58, limit: 90 },
    { name: "Network", usage: 41, limit: 75 }
  ];

  const warnings = metrics.filter(
    metric => metric.usage >= metric.limit
  );

  const averageUsage =
    metrics.reduce((sum, metric) => sum + metric.usage, 0) /
    metrics.length;

  const report = {
    date: new Date().toISOString().split("T")[0],
    averageUsage: `${averageUsage.toFixed(1)}%`,
    monitoredResources: metrics.length,
    warnings: warnings.length,
    status: warnings.length === 0 ? "All systems normal" : "Check resources"
  };

  console.log("Daily Server Report:", report);
}

dailyLog187();
