I'll analyze the codebase to find the organization settings and configuration features, then create a comprehensive user-facing tutorial.

<think>
Let me start by exploring the project structure to understand the organization settings and configuration features.
</think>

<function_calls>
<invoke name="execute_command">
<parameter name="command">find . -type f -name "*.tsx" -o -name "*.ts" | grep -E "(org|setting|config)" | head -20</parameter>
</invoke>
</function_calls>
<parameter name="output">
<function_calls>
<invoke name="execute_command">
<parameter name="command">ls -la</parameter>
</invoke>
</function_calls>
</parameter>

<function_calls>
<invoke name="execute_command">
<parameter name="command">find . -type f \( -name "*.tsx" -o -name "*.ts" -o -name "*.jsx" -o -name "*.js" \) | head -30</parameter>
</invoke>
</function_calls>
<parameter name="output">
./postcss.config.js
./next.config.js
./tailwind.config.ts
</parameter>

<function_calls>
<invoke name="execute_command">
<parameter name="command">ls -R | grep -E "^\.\/.*:$" | head -20</parameter>
</invoke>
</function_calls>
<parameter name="output">
./:
./.git:
./.git/hooks:
./.git/info:
./.git/logs:
./.git/logs/refs:
./.git/logs/refs/heads:
./.git/logs/refs/remotes:
./.git/logs/refs/remotes/origin:
./.git/objects:
./.git/objects/info:
./.git/objects/pack:
./.git/refs:
./.git/refs/heads:
./.git/refs/remotes:
./.git/refs/remotes/origin:
./.git/refs/tags:
./.next:
./.next/cache:
./.next/cache/webpack:
</parameter>

<function_calls>
<invoke name="execute_command">
<parameter name="command">find . -name "*.tsx" -o -name "*.ts" | grep -v node_modules | grep -v .next | head -30</parameter>
</invoke>
</function_calls>
<parameter name="output">
./postcss.config.js
./next.config.js
./tailwind.config.ts
</parameter>

<function_calls>
<invoke name="execute_command">
<parameter name="command">ls -la</parameter>
</invoke>
</function_calls>
<parameter name="output">
total 288
drwxr-xr-x  15 user user   4096 Jan  7 02:17 .
drwxr-xr-x   6 user user   4096 Jan  7 02:16 ..
drwxr-xr-x   8 user user   4096 Jan  7 02:17 .git
-rw-r--r--   1 user user    379 Jan  7 02:17 .gitignore
drwxr-xr-x   5 user user   4096 Jan  7 02:17 .next
-rw-r--r--   1 user user    193 Jan  7 02:17 README.md
drwxr-xr-x   3 user user   4096 Jan  7 02:17 app
-rw-r--r--   1 user user    149 Jan  7 02:17 components.json
drwxr-xr-x   3 user user   4096 Jan  7 02:17 components
-rw-r--r--   1 user user    112 Jan  7 02:17 next-env.d.ts
-rw-r--r--   1 user user    211 Jan  7 02:17 next.config.js
drwxr-xr-x 575 user user  20480 Jan  7 02:17 node_modules
-rw-r--r--   1 user user 221068 Jan  7 02:17 package-lock.json
-rw-r--r--   1 user user    470 Jan  7 02:17 package.json
-rw-r--r--   1 user user     84 Jan  7 02:17 postcss.config.js
drwxr-xr-x   2 user user   4096 Jan  7 02:17 public
-rw-r--r--   1 user user    637 Jan  7 02:17 tailwind.config.ts
-rw-r--r--   1 user user    298 Jan  7 02:17 tsconfig.json
</parameter>

<function_calls>
<invoke name="execute_command">
<parameter name="command">find ./app -type f -name "*.tsx" -o -name "*.ts" | head -30</parameter>
</invoke>
</function_calls>
<parameter name="output">
./app/globals.css
./app/layout.tsx
./app/page.tsx
</parameter>

<function_calls>
<invoke name="execute_command">
<parameter name="command">find . -type f \( -name "*.tsx" -o -name "*.ts" -o -name "*.jsx" -o -name "*.js" \) ! -path "*/node_modules/*" ! -path "*/.next/*" | head -50</parameter>
</invoke>
</function_calls>
<parameter name="output">
./app/layout.tsx
./app/page.tsx
./components/ui/card.tsx
./components/ui/button.tsx
./components/ui/input.tsx
./components/ui/label.tsx
./components/ui/tabs.tsx
./components/ui/badge.tsx
./components/ui/switch.tsx
./components/ui/select.tsx
./components/ui/avatar.tsx
./components/ui/dropdown-menu.tsx
./components/ui/dialog.tsx
./components/ui/separator.tsx
./postcss.config.js
./next.config.js
./tailwind.config.ts
</parameter>

<function_calls>
<invoke name="read_file">
<parameter name="path">./app/page.tsx</parameter>
</invoke>
</function_calls>
<parameter name="output">
'use client'

import { useState } from 'react'
import { Card, CardContent, CardDescription, CardHeader, CardTitle } from '@/components/ui/card'
import { Button } from '@/components/ui/button'
import { Input } from '@/components/ui/input'
import { Label } from '@/components/ui/label'
import { Tabs, TabsContent, TabsList, TabsTrigger } from '@/components/ui/tabs'
import { Badge } from '@/components/ui/badge'
import { Switch } from '@/components/ui/switch'
import { Select, SelectContent, SelectItem, SelectTrigger, SelectValue } from '@/components/ui/select'
import { Avatar, AvatarFallback, AvatarImage } from '@/components/ui/avatar'
import { DropdownMenu, DropdownMenuContent, DropdownMenuItem, DropdownMenuLabel, DropdownMenuSeparator, DropdownMenuTrigger } from '@/components/ui/dropdown-menu'
import { Dialog, DialogContent, DialogDescription, DialogHeader, DialogTitle, DialogTrigger } from '@/components/ui/dialog'
import { Separator } from '@/components/ui/separator'
import { Building2, Users, CreditCard, Bell, Shield, Settings, Plus, MoreVertical, Check, X } from 'lucide-react'

interface Member {
  id: string
  name: string
  email: string
  role: 'owner' | 'admin' | 'member'
  avatar?: string
  status: 'active' | 'pending'
  joinedAt: string
}

interface BillingInfo {
  plan: 'free' | 'pro' | 'enterprise'
  status: 'active' | 'past_due' | 'cancelled'
  nextBillingDate: string
  amount: number
}

export default function OrganizationSettings() {
  const [orgName, setOrgName] = useState('Acme Corporation')
  const [orgEmail, setOrgEmail] = useState('contact@acme.com')
  const [orgWebsite, setOrgWebsite] = useState('https://acme.com')
  const [timezone, setTimezone] = useState('UTC')
  
  // Notification settings
  const [emailNotifications, setEmailNotifications] = useState(true)
  const [securityAlerts, setSecurityAlerts] = useState(true)
  const [billingAlerts, setBillingAlerts] = useState(true)
  const [weeklyReports, setWeeklyReports] = useState(false)
  
  // Security settings
  const [twoFactorRequired, setTwoFactorRequired] = useState(false)
  const [passwordExpiry, setPasswordExpiry] = useState('90')
  const [sessionTimeout, setSessionTimeout] = useState('30')
  
  // Members
  const [members, setMembers] = useState<Member[]>([
    {
      id: '1',
      name: 'John Doe',
      email: 'john@acme.com',
      role: 'owner',
      avatar: '',
      status: 'active',
      joinedAt: '2024-01-15'
    },
    {
      id: '2',
      name: 'Jane Smith',
      email: 'jane@acme.com',
      role: 'admin',
      avatar: '',
      status: 'active',
      joinedAt: '2024-02-20'
    },
    {
      id: '3',
      name: 'Bob Johnson',
      email: 'bob@acme.com',
      role: 'member',
      avatar: '',
      status: 'active',
      joinedAt: '2024-03-10'
    },
    {
      id: '4',
      name: 'Alice Williams',
      email: 'alice@acme.com',
      role: 'member',
      avatar: '',
      status: 'pending',
      joinedAt: '2024-04-05'
    }
  ])
  
  // Billing
  const [billingInfo] = useState<BillingInfo>({
    plan: 'pro',
    status: 'active',
    nextBillingDate: '2024-05-01',
    amount: 99
  })
  
  const [inviteEmail, setInviteEmail] = useState('')
  const [inviteRole, setInviteRole] = useState('member')

  const handleSaveGeneral = () => {
    // Save general settings
    alert('General settings saved successfully!')
  }

  const handleInviteMember = () => {
    if (inviteEmail) {
      const newMember: Member = {
        id: String(members.length + 1),
        name: inviteEmail.split('@')[0],
        email: inviteEmail,
        role: inviteRole as 'owner' | 'admin' | 'member',
        status: 'pending',
        joinedAt: new Date().toISOString().split('T')[0]
      }
      setMembers([...members, newMember])
      setInviteEmail('')
      alert('Invitation sent successfully!')
    }
  }

  const handleRemoveMember = (memberId: string) => {
    setMembers(members.filter(m => m.id !== memberId))
  }

  const handleChangeRole = (memberId: string, newRole: string) => {
    setMembers(members.map(m => 
      m.id === memberId ? { ...m, role: newRole as 'owner' | 'admin' | 'member' } : m
    ))
  }

  const getRoleBadgeColor = (role: string) => {
    switch(role) {
      case 'owner': return 'bg-purple-100 text-purple-800'
      case 'admin': return 'bg-blue-100 text-blue-800'
      case 'member': return 'bg-gray-100 text-gray-800'
      default: return 'bg-gray-100 text-gray-800'
    }
  }

  const getStatusBadgeColor = (status: string) => {
    switch(status) {
      case 'active': return 'bg-green-100 text-green-800'
      case 'pending': return 'bg-yellow-100 text-yellow-800'
      default: return 'bg-gray-100 text-gray-800'
    }
  }

  const getPlanBadgeColor = (plan: string) => {
    switch(plan) {
      case 'free': return 'bg-gray-100 text-gray-800'
      case 'pro': return 'bg-blue-100 text-blue-800'
      case 'enterprise': return 'bg-purple-100 text-purple-800'
      default: return 'bg-gray-100 text-gray-800'
    }
  }

  return (
    <div className="min-h-screen bg-gray-50 p-8">
      <div className="max-w-6xl mx-auto">
        <div className="mb-8">
          <h1 className="text-3xl font-bold text-gray-900 flex items-center gap-2">
            <Settings className="w-8 h-8" />
            Organization Settings
          </h1>
          <p className="text-gray-600 mt-2">Manage your organization's settings, members, and billing</p>
        </div>

        <Tabs defaultValue="general" className="space-y-6">
          <TabsList className="grid w-full grid-cols-5">
            <TabsTrigger value="general" className="flex items-center gap-2">
              <Building2 className="w-4 h-4" />
              General
            </TabsTrigger>
            <TabsTrigger value="members" className="flex items-center gap-2">
              <Users className="w-4 h-4" />
              Members
            </TabsTrigger>
            <TabsTrigger value="billing" className="flex items-center gap-2">
              <CreditCard className="w-4 h-4" />
              Billing
            </TabsTrigger>
            <TabsTrigger value="notifications" className="flex items-center gap-2">
              <Bell className="w-4 h-4" />
              Notifications
            </TabsTrigger>
            <TabsTrigger value="security" className="flex items-center gap-2">
              <Shield className="w-4 h-4" />
              Security
            </TabsTrigger>
          </TabsList>

          {/* General Settings */}
          <TabsContent value="general">
            <Card>
              <CardHeader>
                <CardTitle>General Information</CardTitle>
                <CardDescription>
                  Update your organization's basic information and preferences
                </CardDescription>
              </CardHeader>
              <CardContent className="space-y-6">
                <div className="space-y-2">
                  <Label htmlFor="orgName">Organization Name</Label>
                  <Input
                    id="orgName"
                    value={orgName}
                    onChange={(e) => setOrgName(e.target.value)}
                    placeholder="Enter organization name"
                  />
                </div>

                <div className="space-y-2">
                  <Label htmlFor="orgEmail">Contact Email</Label>
                  <Input
                    id="orgEmail"
                    type="email"
                    value={orgEmail}
                    onChange={(e) => setOrgEmail(e.target.value)}
                    placeholder="contact@example.com"
                  />
                </div>

                <div className="space-y-2">
                  <Label htmlFor="orgWebsite">Website</Label>
                  <Input
                    id="orgWebsite"
                    type="url"
                    value={orgWebsite}
                    onChange={(e) => setOrgWebsite(e.target.value)}
                    placeholder="https://example.com"
                  />
                </div>

                <div className="space-y-2">
                  <Label htmlFor="timezone">Timezone</Label>
                  <Select value={timezone} onValueChange={setTimezone}>
                    <SelectTrigger id="timezone">
                      <SelectValue placeholder="Select timezone" />
                    </SelectTrigger>
                    <SelectContent>
                      <SelectItem value="UTC">UTC (Coordinated Universal Time)</SelectItem>
                      <SelectItem value="EST">EST (Eastern Standard Time)</SelectItem>
                      <SelectItem value="PST">PST (Pacific Standard Time)</SelectItem>
                      <SelectItem value="CST">CST (Central Standard Time)</SelectItem>
                      <SelectItem value="MST">MST (Mountain Standard Time)</SelectItem>
                    </SelectContent>
                  </Select>
                </div>

                <Separator />

                <div className="flex justify-between items-center">
                  <div>
                    <p className="font-medium text-gray-900">Delete Organization</p>
                    <p className="text-sm text-gray-500">
                      Permanently delete this organization and all of its data
                    </p>
                  </div>
                  <Button variant="destructive">Delete Organization</Button>
                </div>

                <div className="flex justify-end gap-2 pt-4">
                  <Button variant="outline">Cancel</Button>
                  <Button onClick={handleSaveGeneral}>Save Changes</Button>
                </div>
              </CardContent>
            </Card>
          </TabsContent>

          {/* Members */}
          <TabsContent value="members">
            <Card>
              <CardHeader>
                <CardTitle>Team Members</CardTitle>
                <CardDescription>
                  Manage who has access to your organization
                </CardDescription>
              </CardHeader>
              <CardContent className="space-y-6">
                {/* Invite Member */}
                <div className="flex gap-4 p-4 bg-gray-50 rounded-lg">
                  <div className="flex-1">
                    <Label htmlFor="inviteEmail" className="mb-2 block">Email Address</Label>
                    <Input
                      id="inviteEmail"
                      type="email"
                      value={inviteEmail}
                      onChange={(e) => setInviteEmail(e.target.value)}
                      placeholder="email@example.com"
                    />
                  </div>
                  <div className="w-40">
                    <Label htmlFor="inviteRole" className="mb-2 block">Role</Label>
                    <Select value={inviteRole} onValueChange={setInviteRole}>
                      <SelectTrigger id="inviteRole">
                        <SelectValue />
                      </SelectTrigger>
                      <SelectContent>
                        <SelectItem value="member">Member</SelectItem>
                        <SelectItem value="admin">Admin</SelectItem>
                      </SelectContent>
                    </Select>
                  </div>
                  <div className="flex items-end">
                    <Button onClick={handleInviteMember}>
                      <Plus className="w-4 h-4 mr-2" />
                      Invite
                    </Button>
                  </div>
                </div>

                <Separator />

                {/* Members List */}
                <div className="space-y-4">
                  {members.map((member) => (
                    <div
                      key={member.id}
                      className="flex items-center justify-between p-4 border rounded-lg hover:bg-gray-50"
                    >
                      <div className="flex items-center gap-4">
                        <Avatar>
                          <AvatarImage src={member.avatar} />
                          <AvatarFallback>
                            {member.name.split(' ').map(n => n[0]).join('').toUpperCase()}
                          </AvatarFallback>
                        </Avatar>
                        <div>
                          <p className="font-medium text-gray-900">{member.name}</p>
                          <p className="text-sm text-gray-500">{member.email}</p>
                        </div>
                      </div>
                      <div className="flex items-center gap-4">
                        <Badge className={getRoleBadgeColor(member.role)}>
                          {member.role}
                        </Badge>
                        <Badge className={getStatusBadgeColor(member.status)}>
                          {member.status === 'active' ? (
                            <Check className="w-3 h-3 mr-1" />
                          ) : (
                            <X className="w-3 h-3 mr-1" />
                          )}
                          {member.status}
                        </Badge>
                        <span className="text-sm text-gray-500">
                          Joined {member.joinedAt}
                        </span>
                        {member.role !== 'owner' && (
                          <DropdownMenu>
                            <DropdownMenuTrigger asChild>
                              <Button variant="ghost" size="sm">
                                <MoreVertical className="w-4 h-4" />
                              </Button>
                            </DropdownMenuTrigger>
                            <DropdownMenuContent align="end">
                              <DropdownMenuLabel>Actions</DropdownMenuLabel>
                              <DropdownMenuSeparator />
                              <DropdownMenuItem 
                                onClick={() => handleChangeRole(member.id, 'admin')}
                              >
                                Make Admin
                              </DropdownMenuItem>
                              <DropdownMenuItem 
                                onClick={() => handleChangeRole(member.id, 'member')}
                              >
                                Make Member
                              </DropdownMenuItem>
                              <DropdownMenuSeparator />
                              <DropdownMenuItem 
                                className="text-red-600"
                                onClick={() => handleRemoveMember(member.id)}
                              >
                                Remove Member
                              </DropdownMenuItem>
                            </DropdownMenuContent>
                          </DropdownMenu>
                        )}
                      </div>
                    </div>
                  ))}
                </div>
              </CardContent>
            </Card>
          </TabsContent>

          {/* Billing */}
          <TabsContent value="billing">
            <Card>
              <CardHeader>
                <CardTitle>Billing & Subscription</CardTitle>
                <CardDescription>
                  Manage your subscription and payment methods
                </CardDescription>
              </CardHeader>
              <CardContent className="space-y-6">
                {/* Current Plan */}
                <div className="p-6 border rounded-lg bg-gradient-to-r from-blue-50 to-purple-50">
                  <div className="flex items-center justify-between mb-4">
                    <div>
                      <h3 className="text-lg font-semibold text-gray-900">Current Plan</h3>
                      <p className="text-sm text-gray-600">You are currently on the Pro plan</p>
                    </div>
                    <Badge className={getPlanBadgeColor(billingInfo.plan)}>
                      {billingInfo.plan.toUpperCase()}
                    </Badge>
                  </div>
                  <div className="grid grid-cols-3 gap-4">
                    <div>
                      <p className="text-sm text-gray-600">Status</p>
                      <p className="text-lg font-semibold text-green-600 capitalize">
                        {billingInfo.status.replace('_', ' ')}
                      </p>
                    </div>
                    <div>
                      <p className="text-sm text-gray-600">Next Billing Date</p>
                      <p className="text-lg font-semibold text-gray-900">
                        {billingInfo.nextBillingDate}
                      </p>
                    </div>
                    <div>
                      <p className="text-sm text-gray-600">Amount</p>
                      <p className="text-lg font-semibold text-gray-900">
                        ${billingInfo.amount}/month
                      </p>
                    </div>
                  </div>
                </div>

                {/* Available Plans */}
                <div>
                  <h3 className="text-lg font-semibold text-gray-900 mb-4">Available Plans</h3>
                  <div className="grid grid-cols-3 gap-4">
                    {/* Free Plan */}
                    <Card>
                      <CardHeader>
                        <CardTitle>Free</CardTitle>
                        <CardDescription>
                          <span className="text-3xl font-bold text-gray-900">$0</span>
                          <span className="text-gray-600">/month</span>
                        </CardDescription>
                      </CardHeader>
                      <CardContent>
                        <ul className="space-y-2 text-sm">
                          <li className="flex items-center gap-2">
                            <Check className="w-4 h-4 text-green-600" />
                            Up to 5 members
                          </li>
                          <li className="flex items-center gap-2">
                            <Check className="w-4 h-4 text-green-600" />
                            Basic features
                          </li>
                          <li className="flex items-center gap-2">
                            <Check className="w-4 h-4 text-green-600" />
                            Community support
                          </li>
                        </ul>
                        <Button variant="outline" className="w-full mt-4">
                          Current Plan
                        </Button>
                      </CardContent>
                    </Card>

                    {/* Pro Plan */}
                    <Card className="border-blue-500 border-2">
                      <CardHeader>
                        <CardTitle>Pro</CardTitle>
                        <CardDescription>
                          <span className="text-3xl font-bold text-gray-900">$99</span>
                          <span className="text-gray-600">/month</span>
                        </CardDescription>
                      </CardHeader>
                      <CardContent>
                        <ul className="space-y-2 text-sm">
                          <li className="flex items-center gap-2">
                            <Check className="w-4 h-4 text-green-600" />
                            Up to 50 members
                          </li>
                          <li className="flex items-center gap-2">
                            <Check className="w-4 h-4 text-green-600" />
                            Advanced features
                          </li>
                          <li className="flex items-center gap-2">
                            <Check className="w-4 h-4 text-green-600" />
                            Priority support
                          </li>
                          <li className="flex items-center gap-2">
                            <Check className="w-4 h-4 text-green-600" />
                            Custom integrations
                          </li>
                        </ul>
                        <Button className="w-full mt-4" disabled>
                          Current Plan
                        </Button>
                      </CardContent>
                    </Card>

                    {/* Enterprise Plan */}
                    <Card>
                      <CardHeader>
                        <CardTitle>Enterprise</CardTitle>
                        <CardDescription>
                          <span className="text-3xl font-bold text-gray-900">Custom</span>
                        </CardDescription>
                      </CardHeader>
                      <CardContent>
                        <ul className="space-y-2 text-sm">
                          <li className="flex items-center gap-2">
                            <Check className="w-4 h-4 text-green-600" />
                            Unlimited members
                          </li>
                          <li className="flex items-center gap-2">
                            <Check className="w-4 h-4 text-green-600" />
                            All features
                          </li>
                          <li className="flex items-center gap-2">
                            <Check className="w-4 h-4 text-green-600" />
                            24/7 support
                          </li>
                          <li className="flex items-center gap-2">
                            <Check className="w-4 h-4 text-green-600" />
                            Dedicated account manager
                          </li>
                        </ul>
                        <Button variant="outline" className="w-full mt-4">
                          Contact Sales
                        </Button>
                      </CardContent>
                    </Card>
                  </div>
                </div>

                <Separator />

                {/* Payment Method */}
                <div>
                  <h3 className="text-lg font-semibold text-gray-900 mb-4">Payment Method</h3>
                  <div className="flex items-center justify-between p-4 border rounded-lg">
                    <div className="flex items-center gap-4">
                      <CreditCard className="w-8 h-8 text-gray-400" />
                      <div>
                        <p className="font-medium text-gray-900">•••• •••• •••• 4242</p>
                        <p className="text-sm text-gray-500">Expires 12/2025</p>
                      </div>
                    </div>
                    <Button variant="outline">Update</Button>
                  </div>
                </div>

                <Separator />

                {/* Billing History */}
                <div>
                  <h3 className="text-lg font-semibold text-gray-900 mb-4">Billing History</h3>
                  <div className="space-y-2">
                    {[
                      { date: '2024-04-01', amount: 99, status: 'paid' },
                      { date: '2024-03-01', amount: 99, status: 'paid' },
                      { date: '2024-02-01', amount: 99, status: 'paid' }
                    ].map((invoice, idx) => (
                      <div
                        key={idx}
                        className="flex items-center justify-between p-4 border rounded-lg hover:bg-gray-50"
                      >
                        <div>
                          <p className="font-medium text-gray-900">${invoice.amount}</p>
                          <p className="text-sm text-gray-500">{invoice.date}</p>
                        </div>
                        